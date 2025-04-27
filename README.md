# 用户服务 API

一个使用 Go、Gin 构建的简单 RESTful 用户服务，遵循清洁架构原则。

## 项目结构

```
├── cmd/                # 主要应用程序
│   └── server/         # 服务器启动
│       └── main.go     # 主函数
├── internal/           # 私有应用程序代码
│   ├── api/            # API 处理器
│   ├── config/         # 配置管理
│   ├── model/          # 数据模型
│   ├── repository/     # 数据访问层
│   └── service/        # 业务逻辑
├── pkg/                # 公共可复用代码
├── configs/            # 配置文件
├── scripts/            # 脚本文件
├── deployments/        # 部署文件
│   ├── docker/         # Docker文件
│   │   └── Dockerfile  # 应用程序Dockerfile
│   └── docker-compose.yml  # Docker Compose配置
├── .github/            # GitHub相关配置
│   └── workflows/      # GitHub Actions工作流
│       └── deploy.yml  # 部署工作流
```

## 开始使用

### 前提条件

- Go 1.20 或更高版本
- Docker 和 Docker Compose（可选，用于容器化部署）
- Make（用于执行 Makefile 命令）

### 使用 Makefile

项目使用 Makefile 来管理常用命令。以下是可用的命令：

```bash
# 显示帮助信息
make help

# 编译项目
make build

# 运行项目
make run

# 使用热重载运行开发环境
make dev

# 更新依赖
make deps

# 清理编译文件
make clean

# 运行测试
make test

# 生成测试覆盖率报告
make cover

# 运行代码检查
make lint

# 生成 Swagger 文档
make swagger

# 安装开发工具
make install-tools

# 生成 Mock 代码
make mock

# 构建 Docker 镜像
make docker

# 使用 Docker Compose 运行项目
make docker-compose
```

### 本地运行

1. 克隆仓库
   ```bash
   git clone https://github.com/your-username/user-service.git
   cd user-service
   ```

2. 安装依赖
   ```bash
   make deps
   ```

3. 安装开发工具
   ```bash
   make install-tools
   ```

4. 生成 Swagger 文档
   ```bash
   make swagger
   ```

5. 运行应用程序
   ```bash
   make run
   ```

   或使用热重载开发模式：
   ```bash
   make dev
   ```

6. API 将在 http://localhost:8080 可用

   Swagger 文档可以通过 http://localhost:8080/swagger/index.html 访问

### 使用 Docker 运行

1. 构建 Docker 镜像
   ```bash
   make docker
   ```

2. 使用 Docker Compose 运行
   ```bash
   make docker-compose
   ```

3. API 将在 http://localhost:8080 可用

## API 端点

### 用户

- `GET /api/v1/users` - 列出所有用户
- `GET /api/v1/users/:id` - 通过 ID 获取用户
- `POST /api/v1/users` - 创建新用户
- `PUT /api/v1/users/:id` - 更新用户
- `DELETE /api/v1/users/:id` - 删除用户

### 认证

- `POST /api/v1/auth/signin` - 用户登录
- `POST /api/v1/auth/signup` - 用户注册

### 健康检查

- `GET /api/v1/health` - API 健康检查

## 开发

### 添加新功能

1. 在适当的目录创建新文件
2. 实现功能
3. 添加测试
4. 运行测试和代码检查
   ```bash
   make test
   make lint
   ```
5. 更新 Swagger 文档
   ```bash
   make swagger
   ```

## 部署

该项目包含用于 CI/CD 的 GitHub Actions 工作流，它会：

1. 运行测试
2. 构建应用程序
3. 创建 Docker 镜像
4. 推送到 Docker Hub
5. 部署到生产环境（占位步骤）

## 许可证

本项目采用 MIT 许可证授权。
