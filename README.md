# gRPC Go
[gRPC](https://grpc.io/docs/languages/go/quickstart/)

## 环境准备
### 安装protobuf
```shell
sudo apt-get update
sudo apt-get install protobuf-compiler
```

### 安装 protoc-gen-go 插件
```bash
go install google.golang.org/protobuf/cmd/protoc-gen-go@v1.28
go install google.golang.org/grpc/cmd/protoc-gen-go-grpc@v1.2
```

### 将 Go 二进制文件的安装路径添加到 PATH
```bash
vim ~/.bashrc
export PATH="$PATH:$(go env GOPATH)/bin"
```
```zsh
vim ~/.zshrc
export PATH="$PATH:$(go env GOPATH)/bin"
```

## 初始化
```shell
go mod init chenjinxin/grpc/examples
go mod tidy
```

## 更新gRPC服务
1. helloworld/helloworld/helloworld.proto
2. helloworld/greeter_server/main.go
3. helloworld/greeter_client/main.go

### 生成proto文件
```shell
protoc --go_out=. --go_opt=paths=source_relative \
    --go-grpc_out=. --go-grpc_opt=paths=source_relative \
    helloworld/helloworld/helloworld.proto
```

### Run
```bash
go run helloworld/greeter_server/main.go
```
```bash
go run helloworld/greeter_client/main.go
go run helloworld/greeter_client/main.go --name=Alice
```