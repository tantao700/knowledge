# 在GO中设置开发/Debug环境

# Windows
- 系统环境设置
    - GOPATH=C:\Users\Xxx\go;D:\Workspace\goproject
    - GOROOT=C:\Go

- Go 开发环境 目录结构

    **目录结果是强制的** 所以项目完全按照这个结构来进行开发

    ```shell
    workspace
    ├─.vscode
    │    ├─setting.json
    │    └─launch.json
    ├─bin
    ├─pkg
    │  └─windows_amd64
    └─src
        ├─hello
        │    ├─hello1.go
        │    └─hello.go
        └─main    
            └─main.go    
    ```    
- 安装插件    
    - [Code Runner](https://marketplace.visualstudio.com/items?itemName=formulahendry.code-runner) 代码运行插件
    - [Go](https://marketplace.visualstudio.com/items?itemName=ms-vscode.Go)  编辑器插件

- Debug设置 **.vscode/launch.json**
```json
{
    // Use IntelliSense to learn about possible attributes.
    // Hover to view descriptions of existing attributes.
    // For more information, visit: https://go.microsoft.com/fwlink/?linkid=830387
    "version": "0.2.0",
    "configurations": [
        {
            "name": "Launch_main",
            "type": "go",
            "request": "launch",
            "mode": "auto",
            "program": "${workspaceFolder}/src/main",
            "env": {},
            "args": [],
            "showLog": false
        }
    ]
}
```

- 编辑器设置 **.vscode/setting.json**

```json
{
    "go.toolsGopath": "C:\\Users\\Xxx\\go",
    "go.gopath": "C:\\Users\\Xxx\\go;D:\\Sources\\go\\hello",
    "go.autocompleteUnimportedPackages": true,
    "code-runner.executorMap": {
        "go": "set GOPATH=C:\\Users\\Xxx\\go;D:\\Sources\\go\\hello&& go run"
    }
}
```

```console
[Running] set GOPATH=C:\Users\Xxx\go;D:\Sources\go\hello&& go run "d:\Sources\go\hello\src\main\main.go"
SayHello()-->Hello
SayHello()-->Hello2
SayWorld()-->World
SayHello()-->Hello
SayHello()-->Hello2
SayHello()-->Hello
SayHello()-->Hello2
SayWorld()-->World---3
SayWorld()-->World---3.2

[Done] exited with code=0 in 3.916 seconds
```

按照以上的设置就能够 在VsCode上进行


