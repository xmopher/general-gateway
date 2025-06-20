# Mo Gateway

### 配置要求

- JDK 21
- Maven 3.8+
- Docker
- Redis


## 📖 项目介绍

Mo Gateway 是一个轻量级、高性能的 API 网关服务，基于 Spring Boot 3.x 和 Spring Cloud 构建。它提供了丰富的功能集，包括高性能的请求路由、智能负载均衡、灵活的限流策略、服务发现、安全控制等，是构建现代化微服务架构的理想选择。

### 系统架构

```
                                    ┌─────────────┐
                                    │   Client    │
                                    └──────┬──────┘
                                           │
                                           ▼
┌─────────────────────────────────────────────────────────────┐
│                        Mo Gateway                           │
│  ┌─────────────┐  ┌─────────────┐  ┌─────────────────────┐  │
│  │  路由模块    │  │  限流模块    │  │    负载均衡模块     │  │
│  └─────────────┘  └─────────────┘  └─────────────────────┘  │
│                                                             │
│  ┌─────────────┐  ┌─────────────┐  ┌─────────────────────┐  │
│  │  安全模块    │  │  监控模块    │  │    服务发现模块     │  │
│  └─────────────┘  └─────────────┘  └─────────────────────┘  │
└─────────────────────────────────────────────────────────────┘
                                           │
                                           ▼
                                    ┌─────────────┐
                                    │  Services   │
                                    └─────────────┘
```

### 🌟 核心特性

#### 1. 高性能请求处理
- 采用 Spring WebFlux 响应式编程模型，提供卓越的性能表现
- 支持 HTTP/2 协议，实现更高效的网络传输
- 异步非阻塞 I/O 处理，提高系统吞吐量
- 智能的请求压缩和缓存策略，优化响应时间

#### 2. 智能负载均衡
- 提供多种负载均衡算法，满足不同场景需求
  - 轮询算法：适用于服务实例性能相近的场景
  - 加权轮询：支持服务实例差异化配置
  - 最少连接：适用于长连接场景
  - 响应时间加权：根据服务响应时间动态调整
- 自动服务健康检查，及时剔除异常实例
- 支持动态调整服务权重，实现更精细的流量控制

#### 3. 灵活的限流策略
- 基于 Redis 的分布式限流，支持集群部署
- 多种限流算法支持，适应不同业务场景
  - 令牌桶：适合突发流量场景
  - 漏桶：适合平滑流量场景
  - 滑动窗口：适合精确控制场景
- 支持服务级别、接口级别的限流配置
- 提供限流降级策略，保证系统可用性

#### 4. 服务发现与注册
- 原生支持 Kubernetes 服务发现
- 提供自定义服务注册机制
- 支持动态服务上下线
- 服务元数据管理，支持服务标签和属性配置

#### 5. 安全特性
- 完整的 SSL/TLS 加密支持
- 灵活的认证授权机制
- API 密钥管理
- 请求签名验证
- 可配置的 CORS 策略

#### 6. 监控与可观测性
- 集成 Prometheus 监控系统
- 详细的请求追踪
- 丰富的性能指标
- 完善的健康检查机制
- 结构化的日志记录

## 🚀 快速开始

### 环境要求
- JDK 21
- Maven 3.8+
- Docker 和 Docker Compose
- Redis 7.x
- Kubernetes（可选，用于生产环境）

### 本地开发环境搭建
1. 克隆项目代码
2. 启动依赖服务（Redis等）
3. 构建并运行项目
4. 验证服务是否正常运行

## ⚙️ 配置说明

### 基础配置
网关服务支持丰富的配置选项，包括：
- 服务端口配置
- SSL/TLS 配置
- HTTP/2 支持
- 限流参数配置
- 负载均衡策略
- 服务发现配置

详细配置说明请参考 [配置指南](docs/configuration.md)

### 环境变量
支持通过环境变量覆盖默认配置，主要配置项包括：
- 服务发现类型
- Redis 连接信息
- 限流参数
- 日志级别
- 监控配置

## 🔌 业务服务接入指南

### 服务接入流程
1. 服务注册
   - Kubernetes 环境配置
   - 非 Kubernetes 环境配置
2. 限流配置
3. 负载均衡配置
4. 监控集成

详细接入说明请参考 [服务接入指南](docs/integration.md)

## 🐳 部署指南

### 部署方式
1. Docker 部署
   - 单机部署
   - 集群部署
2. Kubernetes 部署
   - 基础部署
   - 高可用部署

详细部署说明请参考 [部署指南](docs/deployment.md)

## 📊 监控与运维

### 监控指标
- 服务健康状态
- 性能指标
- 限流统计
- 系统资源使用情况

### 日志管理
- 结构化日志
- 日志收集
- 日志分析

详细运维说明请参考 [运维指南](docs/operation.md)

## 🤝 贡献指南

欢迎贡献代码，提交 Issue 或 Pull Request。请确保：
1. 遵循代码规范
2. 添加必要的测试
3. 更新相关文档

详细贡献指南请参考 [贡献指南](docs/contributing.md)

## 📝 许可证

本项目采用 MIT 许可证

## 📞 联系方式

- 项目维护者：[Mo]
- 邮箱：[xmopher@hotmail.com]
- 项目链接：[https://github.com/xmopher/gateway.git]