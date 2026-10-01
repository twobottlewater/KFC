# OpenCode CLI 安装教程

## 安装前准备

在安装 OpenCode CLI 之前，需要确保系统已安装 Node.js 和 npm。

### 检查 Node.js 和 npm 版本

打开 PowerShell 终端，分别运行以下命令检查版本：

```powershell
# 检查 Node.js 版本
node -v

# 检查 npm 版本
npm -v
```

如果输出了版本号，则说明已安装成功。本教程中使用的版本：
- Node.js: v24.13.0
- npm: 11.6.2

### 安装 Node.js（如果未安装）

如果未安装 Node.js，请按照以下步骤操作：
1. 访问 Node.js 官方网站：https://nodejs.org
2. 下载并安装 LTS 版本（长期支持版本）
3. 安装完成后，重新打开终端并验证版本

## 安装 OpenCode CLI

使用 npm 全局安装 OpenCode CLI：

```powershell
npm install -g opencode-ai
```

## 验证安装成功

安装完成后，运行以下命令检查 OpenCode CLI 版本：

```powershell
opencode --version
```

如果输出了版本号（例如：1.1.29），则说明安装成功。

## 启动 OpenCode

安装成功后，可以通过以下命令启动 OpenCode：

```powershell
opencode
```

## 配置 Provider（可选）

根据需要，可以配置不同的模型提供商。具体配置方法可以参考相关文档。

## 参考信息

- OpenCode 官方文档：https://opencode.ai
- Node.js 官方网站：https://nodejs.org
- 技术爬爬虾 B 站视频教程

## 安装过程总结

1. **检查环境**：确保已安装 Node.js 和 npm
2. **安装 CLI**：使用 npm 全局安装 opencode-ai
3. **验证安装**：运行 opencode --version 检查版本
4. **启动使用**：运行 opencode 命令启动

此教程基于 Windows 系统，在 PowerShell 终端中执行。其他操作系统（如 macOS、Linux）的安装步骤类似，只需使用对应的终端命令。