# microservices

A simple go microservice example

$ psql postgres
$ CREATE DATABASE auth_svc;
$ CREATE DATABASE order_svc;
$ CREATE DATABASE product_svc;
$ \l
$ exit

git submodule add https://github.com/CodingForFunAndProfit/auth.git

cd apigateway
go mod init github.com/CodingForFunAndProfit/apigateway
mkdir -p cmd pkg/config/envs pkg/auth/pb pkg/auth/routes pkg/order/pb pkg/order/routes pkg/product/pb pkg/product/routes
touch Makefile cmd/main.go pkg/config/envs/dev.env pkg/config/config.go
touch pkg/auth/pb/auth.proto pkg/auth/routes/login.go pkg/auth/routes/register.go pkg/auth/client.go pkg/auth/middleware.go pkg/auth/routes.go
touch pkg/product/pb/product.proto pkg/product/routes/create_product.go pkg/product/routes/find_one.go pkg/product/client.go pkg/product/routes.go
touch pkg/order/pb/order.proto pkg/order/routes/create_order.go pkg/order/client.go pkg/product/routes.go

go get github.com/gin-gonic/gin
go get github.com/spf13/viper
go get google.golang.org/grpc
go get -u google.golang.org/protobuf

go get google.golang.org/grpc/cmd/protoc-gen-go-grpc
go install google.golang.org/grpc/cmd/protoc-gen-go-grpc
