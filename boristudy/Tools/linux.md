# linux 命令

## grep

```bash
# 正则匹配（当前路径下的所有文件）
➜ grep -r 'hello'

# 查找多个关键字 - 并集（-E）
➜ grep -E "Error|Panic"

# 查找多个关键字 - 交集（利用通道）
➜ grep word1 file.text|grep word2|grep word3
```
