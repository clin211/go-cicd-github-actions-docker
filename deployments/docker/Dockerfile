FROM golang:1.20-alpine AS builder

WORKDIR /app

# 复制go.mod和go.sum文件
COPY go.mod go.sum* ./

# 下载依赖
RUN go mod download

# 复制源代码
COPY . .

# 构建应用程序
RUN CGO_ENABLED=0 GOOS=linux go build -o /app/server ./cmd/server

# 创建最小的生产镜像
FROM alpine:3.18

WORKDIR /app

# 从构建器阶段复制二进制文件
COPY --from=builder /app/server .
# 复制配置文件
COPY --from=builder /app/configs ./configs

# 暴露端口
EXPOSE 8080

# 运行应用程序
CMD ["/app/server"]
