# 忆罗云算法模型性能测试平台

一个用于测试和分析机器学习算法模型性能的全栈Web应用，提供模型管理、数据集管理、性能测试和结果分析等完整功能。

## 📋 项目概述

本项目是一个综合性的忆罗云算法模型性能测试平台，旨在为机器学习研究者和开发者提供一个完整的模型评估和性能测试解决方案。平台采用前后端分离架构，前端使用Vue.js构建用户界面，后端使用Flask提供RESTful API服务。

### 主要功能

- 🤖 **模型管理**：支持多种机器学习模型的导入、配置和管理
- 📊 **数据集管理**：提供数据集上传、预处理和管理功能
- ⚡ **性能测试**：自动化测试模型的准确率、推理速度、内存使用等性能指标
- 📈 **结果分析**：可视化展示测试结果，支持多种图表和数据导出
- ⚙️ **系统设置**：可配置的测试参数和系统选项

## 🏗️ 技术架构

### 前端技术栈
- **Vue 3**：渐进式JavaScript框架
- **Vue Router 4**：官方路由管理器
- **JavaScript ES6+**：现代JavaScript语法
- **HTML5/CSS3**：网页结构和样式

### 后端技术栈
- **Flask**：轻量级Python Web框架
- **Flask-SQLAlchemy**：SQLAlchemy数据库ORM
- **Flask-CORS**：跨域资源共享支持
- **SQLite**：轻量级关系型数据库

### 开发工具
- **Vue CLI**：Vue项目脚手架工具
- **pnpm**：高效的包管理器
- **Babel**：JavaScript编译器
- **ESLint**：代码质量检查工具

## 📁 项目结构

```
algorithmic-model-testing 3/
├── backend/                    # 后端服务
│   ├── app.py                 # Flask应用主文件
│   ├── run.py                 # 应用启动脚本
│   ├── requirements.txt       # Python依赖列表
│   ├── test_results.db       # SQLite数据库文件
│   └── README.md              # 后端文档
├── frontend/                   # 前端应用
│   ├── public/                # 静态资源目录
│   ├── src/                   # 源代码目录
│   │   ├── assets/           # 资源文件
│   │   ├── components/       # Vue组件
│   │   ├── views/           # 页面视图
│   │   ├── router/          # 路由配置
│   │   ├── workers/         # Web Workers
│   │   ├── App.vue          # 根组件
│   │   └── main.js          # 应用入口
│   ├── package.json          # 项目依赖配置
│   ├── vue.config.js        # Vue配置文件
│   └── README.md            # 前端文档
├── package.json               # 根项目配置
└── README.md                 # 项目文档
```

## 🚀 快速开始

### 环境要求

- **Node.js**：14.0.0 或更高版本
- **Python**：3.8 或更高版本
- **pnpm**：推荐的包管理器

### 后端服务启动

1. 进入后端目录：
   ```bash
   cd backend
   ```

2. 安装Python依赖：
   ```bash
   pip install -r requirements.txt
   ```

3. 启动后端服务：
   ```bash
   python run.py
   ```

   后端服务将运行在 `http://127.0.0.1:5000`

### 前端应用启动

1. 进入前端目录：
   ```bash
   cd frontend
   ```

2. 安装依赖：
   ```bash
   pnpm install
   # 或者使用 npm
   npm install
   ```

3. 启动开发服务器：
   ```bash
   pnpm run serve
   # 或者使用 npm
   npm run serve
   ```

   前端应用将运行在 `http://localhost:8080`

## 📖 功能模块详解

### 1. 首页（Home）
- 项目概览和统计信息
- 最近测试结果展示
- 快速操作入口

### 2. 模型管理（Model Management）
- 支持多种模型格式的上传和导入
- 模型信息编辑和删除
- 模型性能参数配置

### 3. 数据集管理（Dataset Management）
- 数据集文件上传和管理
- 数据预览和基本信息展示
- 数据预处理功能

### 4. 性能测试（Performance Testing）
- 选择模型和数据集进行测试
- 配置测试参数（批次大小、迭代次数等）
- 实时显示测试进度和结果
- 支持后台测试和批量测试

### 5. 结果分析（Results Analysis）
- 测试结果的可视化展示
- 支持多种图表类型（柱状图、折线图、散点图等）
- 结果对比和统计分析
- 数据导出功能（PDF、Excel等格式）

### 6. 系统设置（Settings）
- 系统配置选项
- 用户偏好设置
- 关于页面

## 🔌 API接口文档

### 基础信息
- **基础URL**：`http://127.0.0.1:5000/api`
- **数据格式**：JSON
- **认证方式**：暂无（开发版本）

### 主要接口

#### 1. 保存测试结果
```
POST /api/results
```

请求体示例：
```json
{
  "test_id": "TEST001",
  "model_name": "随机森林分类器",
  "dataset_name": "鸢尾花数据集",
  "metrics": {
    "accuracy": 0.96,
    "precision": 0.95,
    "recall": 0.94,
    "f1": 0.945,
    "auc": 0.98
  },
  "performance": {
    "avgInferenceTime": "12.5",
    "memoryUsage": "45.2",
    "cpuUsage": "25.3",
    "testDuration": "2.3"
  },
  "test_config": {
    "batchSize": 32,
    "iterations": 10,
    "testRatio": 0.2
  }
}
```

#### 2. 获取测试结果列表
```
GET /api/results?page=1&per_page=10&model_name=随机森林&dataset_name=鸢尾花
```

#### 3. 获取统计信息
```
GET /api/stats
```

#### 4. 健康检查
```
GET /api/health
```

## 🗄️ 数据库设计

### TestResult 表结构

| 字段名 | 类型 | 说明 |
|--------|------|------|
| id | Integer | 主键 |
| test_id | String(50) | 测试唯一标识 |
| model_name | String(100) | 模型名称 |
| dataset_name | String(100) | 数据集名称 |
| metrics | JSON | 评估指标 |
| performance | JSON | 性能指标 |
| test_config | JSON | 测试配置 |
| created_at | DateTime | 创建时间 |

## 🎨 界面设计

### 设计原则
- **简洁明了**：界面布局清晰，操作流程简单
- **响应式设计**：支持桌面和移动设备
- **一致性**：保持统一的视觉风格和交互模式
- **可访问性**：遵循Web可访问性标准

### 主要特性
- 侧边导航栏，方便页面切换
- 卡片式布局，信息展示清晰
- 丰富的图表和数据可视化
- 友好的错误提示和加载状态

## 🔧 开发指南

### 代码规范
- 前端遵循Vue.js官方风格指南
- 后端遵循PEP 8 Python编码规范
- 使用ESLint进行代码质量检查
- 提交信息遵循Conventional Commits规范

### 测试
```bash
# 前端测试
cd frontend
npm run test

# 后端测试
cd backend
python -m pytest
```

### 构建
```bash
# 前端构建
cd frontend
npm run build

# 生产环境部署
# 将frontend/dist目录部署到Web服务器
# 配置反向代理指向后端服务
```

## 🚀 部署指南

### 开发环境
- 前端：`http://localhost:8080`
- 后端：`http://127.0.0.1:5000`

### 生产环境部署建议

#### 前端部署
1. 构建生产版本：`npm run build`
2. 将`dist`目录部署到Nginx或Apache
3. 配置反向代理

#### 后端部署
1. 使用Gunicorn或uWSGI作为WSGI服务器
2. 配置Nginx反向代理
3. 使用PostgreSQL或MySQL替代SQLite
4. 添加环境变量配置管理

#### Docker部署
```dockerfile
# 前端Dockerfile示例
FROM node:16-alpine
WORKDIR /app
COPY package*.json ./
RUN npm install
COPY . .
RUN npm run build
FROM nginx:alpine
COPY --from=0 /app/dist /usr/share/nginx/html
```

## 🤝 贡献指南

欢迎贡献代码！请遵循以下步骤：

1. Fork本项目
2. 创建特性分支：`git checkout -b feature/AmazingFeature`
3. 提交更改：`git commit -m 'Add some AmazingFeature'`
4. 推送分支：`git push origin feature/AmazingFeature`
5. 创建Pull Request

## 📝 更新日志

### v1.0.0 (2024-11-27)
- ✨ 初始版本发布
- 🎨 完成基础UI界面
- ⚡ 实现核心功能模块
- 🔌 提供完整的REST API
- 📊 集成数据可视化功能

## 📄 许可证

本项目采用ISC许可证 - 查看 [LICENSE](LICENSE) 文件了解详情。

## 📞 联系方式

如有问题或建议，请通过以下方式联系：

- 📧 邮箱：[your-email@example.com]
- 🐛 问题反馈：[GitHub Issues]
- 💬 讨论：[GitHub Discussions]

## 🙏 致谢

感谢以下开源项目的支持：

- [Vue.js](https://vuejs.org/) - 渐进式JavaScript框架
- [Flask](https://flask.palletsprojects.com/) - Python Web框架
- [Chart.js](https://www.chartjs.org/) - 图表库
- [Element Plus](https://element-plus.org/) - Vue组件库

---

⭐ 如果这个项目对你有帮助，请给它一个星标！
