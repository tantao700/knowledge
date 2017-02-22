# git的相关配置

## 使用git

### 全局设置

```
$ git config --global user.name "T_T"
$ git config --global user.email tantao700@gmail.com
```

配置完成之后会在$HOME目录下生成一个.gitconfig配置文件，具体参考[示例](.gitconfig)。

`--local` 是将这些内容写入 project 下的 .git/config 文件中，每个project都可以有不同的配置

haha just for test