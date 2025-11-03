# Lovrabet 数据集 MCP 服务器 🚀

为 Claude Desktop 提供 Lovrabet 数据集访问的 MCP (Model Context Protocol) 服务器。

![npm](https://img.shields.io/npm/v/@lovrabet/dataset-mcp-server)
![license](https://img.shields.io/github/license/lovrabet/dataset-mcp-server)
![node](https://img.shields.io/node/v/@lovrabet/dataset-mcp-server)

## ✨ 功能特性

- 🤖 **MCP 服务器**：与 Claude Desktop 无缝集成，实现 AI 驱动的数据集探索
- 🔍 **完整的数据集分析**：基于 @lovrabet/dsparser 的全面元数据提取
- 📝 **SDK 代码生成**：自动生成完整的 TypeScript SDK 代码（支持简化和完整两种模式）
- 🔎 **智能搜索**：通过关键词快速查找数据集
- 🔐 **浏览器登录**：安全便捷的浏览器登录流程，Cookie 自动管理
- 🧪 **完整测试覆盖**：44+ 单元测试，确保代码质量
- 📚 **丰富示例**：3 个完整的使用示例，快速上手

## 🚀 快速开始

> 💡 **本地开发者**：想要在本地运行 MCP Server？查看 [快速开始指南](./QUICK_START.md)

### 安装

1. 全局安装 MCP 服务器：

```bash
npm install -g @lovrabet/dataset-mcp-server
```

2. 配置 Claude Desktop（[详细指南](./docs/mcp-setup.md)）：

```json
{
  "mcpServers": {
    "lovrabet-dataset": {
      "command": "lovrabet-dataset-mcp",
      "env": {
        "DEFAULT_APP_CODE": "你的应用代码",
        "DEFAULT_ENV": "online"
      }
    }
  }
}
```

3. 重启 Claude Desktop 开始探索数据集！


## 📖 文档

### 用户文档

- [MCP 设置指南](./docs/mcp-setup.md) - 配置 Claude Desktop 集成
- [快速开始](./QUICK_START.md) - 本地运行 MCP Server 的最快方式
- [示例代码](./examples/README.md) - 完整的使用示例和说明

### 开发文档

- [本地开发指南](./docs/LOCAL_DEVELOPMENT.md) - 如何在本地运行和调试 MCP Server
- [测试指南](./test/README.md) - 单元测试和手动测试说明
- [架构概览](./docs/architecture.md) - 了解项目架构

## 🔐 身份认证

### 浏览器登录流程

项目使用浏览器登录方式，无需在代码中硬编码账号密码：

1. **首次使用时**，调用 `login` tool
2. 系统会在本地启动 HTTPS 服务器，并提供登录 URL
3. 在浏览器中打开 URL，会自动跳转到 Lovrabet 登录页面
4. 登录成功后，Cookie 自动保存到 `~/.lovrabet/cookie`
5. 后续使用会自动读取保存的 Cookie，无需重复登录

### Cookie 管理

- **存储位置**：`~/.lovrabet/cookie`
- **共享使用**：与 `lovrabet-cli` 共享认证状态
- **自动验证**：每次使用前自动检查 Cookie 有效性
- **错误处理**：如果保存失败会明确提示错误原因

## 📚 使用示例

项目提供 3 个完整的示例，展示不同的使用场景：

### 1. 基础使用 (`examples/basic-usage.ts`)

- 数据集列表获取和分析
- 数据集详情查询
- 字段和操作信息展示
- SDK 代码生成

### 2. SDK 代码生成 (`examples/sdk-code-generation.ts`)

- 为不同环境生成代码（online/daily）
- 为不同操作生成代码（create/update/getOne/getList/delete）
- 请求和响应示例
- 完整可运行的 SDK 代码

### 3. 数据集比较 (`examples/compare-datasets.ts`)

- 比较 online 和 daily 环境的数据集
- 识别环境间的差异
- 分析字段和操作变化

### 运行示例

```bash
# 1. 配置 examples/config.json
cp examples/config.example.json examples/config.json
# 编辑 config.json，设置 appCode 和 env

# 2. 运行示例（会自动触发登录流程）
npm run example:basic
npm run example:sdk
npm run example:compare
```

## 🧪 测试

项目包含完整的测试套件，覆盖核心功能：

```bash
# 运行所有测试（44+ 测试用例）
npm test

# 开发模式（监听文件变化）
npm run test:watch

# 可视化测试界面
npm run test:ui

# 生成覆盖率报告
npm run test:coverage
```

### 测试覆盖

- ✅ **认证模块** (20 tests) - Cookie 管理、域名配置
- ✅ **API 客户端** (9 tests) - HTTP 请求、参数验证
- ✅ **数据分析器** (7 tests) - 数据集解析、搜索、SDK 生成
- ✅ **工具函数** (7 tests) - 搜索、环境处理

详细测试文档：[test/README.md](./test/README.md)


## 🙏 致谢
- MCP 支持来自 [@modelcontextprotocol/sdk](https://modelcontextprotocol.io)

## 🆘 支持

- 📖 [文档](./docs)
- 💬 [GitHub Issues](https://github.com/lovrabet-ai/lovrabet-dataset-mcp/issues)
- 📧 邮箱：support@lovrabet.com

## 📄 许可证

**专有软件（Proprietary）** - 详见 [LICENSE](./LICENSE) 文件

本软件为 Lovrabet 开放平台的专有工具：

- ✅ **允许使用** - 可以安装和使用本工具访问 Lovrabet 数据集
- ✅ **集成使用** - 可以集成到您的开发工具链中
- ❌ **不得修改** - 不得修改、反编译或逆向工程
- ❌ **不得再分发** - 不得复制或分发本软件
- ❌ **源代码不公开** - 本软件为闭源软件

如需商业授权或有疑问，请访问 [lovrabet.com](https://www.lovrabet.com)

## 📝 更新日志

### v1.0.8 (最新)

**新功能**

- ✨ 浏览器登录流程：无需硬编码密码，更安全便捷
- ✨ 完整的 SDK 代码生成：支持简化和完整两种模式
- ✨ 环境特定配置：online 环境不输出 env 配置，daily 环境明确标注
- ✨ 3 个完整使用示例：快速上手项目

**改进**

- 🔧 重构 SDK 代码生成：从底层 Operation 类生成完整代码
- 🔧 Cookie 写入失败处理：明确错误提示和恢复建议
- 🔧 统一配置管理：examples 使用 config.json 集中配置
- 🔧 自动登录验证：每次使用前自动检查 session 有效性

---

<p align="center">由 Lovrabet Team 制作</p>
