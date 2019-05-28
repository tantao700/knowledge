# VIM GO

### 命令行模式

| 命令          | 功能                     | 扩展命令            |
| ------------  | ------------------------|---------------------|
| `]]`          | 跳转到下一个function     | `d]]` `3]]`  `v]]`  |
| `[[`          | 跳转到上一个function     | `d[[` `3[[`  `v[[`  |
| `dif`         | 删除function内的内容     | -  |
| `yif`         | 复制function内的内容     | -  |
| `yaf`         | 复制function所有内容     | -  |
| `vaf`         | 选择function所有内容     | -  |
| `vif`         | 选择function所有内容     | -  |

### VIM-GO 模式
| 命令                  | 功能                     |
| ------------------    | ------------------------|
| `:GoDecls`            | 查看所有的定义(func,type)|
| `:GoDeclsDir`         | 查看文件夹中所有的定义(func,type)|
| `:GoBuild`            | 查看文件夹中所有的定义(func,type)|
| `:GoRun`              | 运行Go程序|
| `:GoTest`             | 运行Go测试程序|
| `:GoTestCompile`      | 运行Go测试程序|
| `:GoCoverage`         | 运行Go代码覆盖|
| `:GoCoverageClear`    | 运行Go代码覆盖：go test -coverprofile tempfile|
| `:GoImport `          | import library：GoImport strings|
| `:GoImportAs`         | `:GoImportAs str strings`|
| `:GoDrop`             | `:GoDrop strings`|
| `:GoDef`              | 跳转到类型定义|
| `:GoDoc`              | 查看文档|
| `:GoInfo`             | 查看|
| `:GoFiles`            | 查看那些文件在这个包|
| `:GoDeps`             | 查看文件有哪些依赖包|
| `:GoReferrers`        | 查看文件引用:依赖 guru|
| `:GoDescribe`         | 查看文件引用:依赖 guru|
| `:GoImplements`       | 查看接口实现:依赖 guru|
| `:GoWhicherrs`        | 查看接口实现:依赖 guru|
| `:GoChannelPeers`     | 查看接口实现:依赖 guru|
| `:GoCallees`          | 查看接口实现:依赖 guru|
| `:GoCallstack`        | 查看接口实现:依赖 guru|
| `:GoGuruScope`        | 查看接口实现:依赖 guru|
| `:GoBuildTags`        | 查看接口实现:依赖 guru|
| `:GoFreevars `        | 查看接口实现:依赖 guru|
| `:GoGenerate  `       | call `go generate`|
| `:GoImpl  `           | call `go generate`|
| `:GoPlay  `           | call `go generate`|
| `:GoPath  `           | show go Path|

### 一些快捷键
| 快捷键         | normal | 功能             |
| ------------  | ------ |----------------- |
| `ctrl+]`      | `gd`   | 查看定义/源码     | 
| `ctrl+t`      | -      | 回退定义/源码     | 
| `ctrl+l`      | -      | 取消搜索高亮      | 

### vimrc 配置
| vimrc 配置         | 配置             |
| ------------  | -----------------|
| go-test       | autocmd FileType go nmap <leader>t  <Plug>(go-test)     | 
| go-build      | autocmd FileType go nmap <leader>b  <Plug>(go-build)     | 
| go-coverage-toggle      | autocmd FileType go nmap <Leader>c <Plug>(go-coverage-toggle) |
| go-info      | autocmd FileType go nmap <Leader>i <Plug>(go-info) |
| import      | let g:go_fmt_command = "goimports"     | 
| enable go info      | let g:go_auto_type_info = 1     | 
