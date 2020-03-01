# 自己实现的rollback接口

## 简介

### 背景

对于微服务，尤其是使用了数据库服务的微服务，在处理失败请求时如何保证数据的一致性：数据库可以通过自带的事务操作来保证（`Commit`和`Rollback`），但是RPC之间的调用就难以保证一致性了。

### 方案

> 自己写的一个Rollback接口，还有很多不足之处需要完善。

1. `interface`定义：

```go
package utils  

type RbFunc func()  

type Rollback interface {  
   UseRollback()  
   NeedRollBack()  
   AddRollBack(...RbFunc)  
}  

type RollbackList []RbFunc  

type RollbackHandler struct {  
   needRollback bool  
  rollbackList RollbackList  
}  

func (r *RollbackHandler) UseRollback() {  
   if !r.needRollback {  
      return  
  }  

   for _, rollBackFunc := range r.rollbackList {  
      defer rollBackFunc()  
   }  
}  

func (r *RollbackHandler) AddRollback(rollBackFuncs ...RbFunc) {  
   for _, val := range rollBackFuncs {  
      r.rollbackList = append(r.rollbackList, val)  
   }  
}  

func (r *RollbackHandler) NeedRollback() {  
   r.needRollback = true  
}  

func (r *RollbackHandler) GetRollback() bool {  
   return r.needRollback  
}
```

2. 使用：

```go
type UseRollbackHandler struct {  
   utils.RollbackHandler  
   Ctx   context.Context  
   ...
}
func rollbackFunc_rpcA() utils.RbFunc{}
func rollbackFunc_rpcA() utils.RbFunc{}

func (self *UseRollbackHandler) Execute() error {  
   defer self.UseRollback()
   err := rpcA.Action()
   if err != nil {
       self.NeedRollback()
   }
   self.AddRollback(rollbackFunc_rpcA())
   err = rpcB.Action()
   if err != nil {
       self.NeedRollback()    // 会通过"rollbackFunc_rpcA"回滚前面调用rpcA的执行内容
   }
   self.AddRollback(rollbackFunc_rpcB())
```
