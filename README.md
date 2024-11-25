# 概述
go-micro-case go 微服务项目
# 官方文档
参考：
https://blog.csdn.net/weixin_36865481/article/details/140481869

# 文件


# 相关命令
````
    初始化命令
      -- 进入目录
      cd go-micro-case
      -- 初始化module
      go mod init go-micro-case
    设置下载依赖包的代理
      go env -w GOPROXY=https://proxy.golang.com.cn,direct
    下载构建插件的依赖
      go get github.com/tetratelabs/proxy-wasm-go-sdk
      go get github.com/alibaba/higress/plugins/wasm-go@v1.3.1
      go get github.com/tidwall/gjson
````
源码编写完成后编译
````
go mod tidy
tinygo build -o main-fe.wasm -scheduler=none -target=wasi -gc=custom -tags="custommalloc nottinygc_finalizer" ./main-fe.go
go mod tidy
tinygo build -o main-be.wasm -scheduler=none -target=wasi -gc=custom -tags="custommalloc nottinygc_finalizer" ./api/main-be.go
````



# 注意下事项
1. 需要访问github.com,需要FQ，你懂的
2. 编译生成WASM文件的命令在Windows环境需要调整<br/>
````
&nbsp;&nbsp;&nbsp;&nbsp;tinygo build -o main.wasm -scheduler=none -target=wasi -gc=custom -tags='custommalloc nottinygc_finalizer' ./main.go<br/>
&nbsp;&nbsp;&nbsp;&nbsp;-----><br/>
&nbsp;&nbsp;&nbsp;&nbsp;tinygo build -o main.wasm -scheduler=none -target=wasi -gc=custom -tags="custommalloc nottinygc_finalizer" ./main.go<br/>
````

###最新版本命令
```
go mod tidy
tinygo build -o higress-main.wasm -scheduler=none -target=wasi -gc=custom -tags="custommalloc nottinygc_finalizer" ./higress-main.go
```


版本 1.0.2