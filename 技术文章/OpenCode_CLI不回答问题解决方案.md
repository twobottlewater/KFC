# OpenCode CLI 不回答问题解决方案

## 问题描述

当使用 OpenCode CLI 时，输入内容后没有得到响应，命令执行时间过长且没有输出。

## 问题原因分析

从日志分析来看，OpenCode CLI 正在尝试连接到 Anthropic 的 Claude 模型，但可能由于以下原因导致卡住：

1. **网络连接问题**：无法连接到 Anthropic 的 API 服务器
2. **API 密钥配置问题**：没有正确配置 API 密钥
3. **模型访问权限问题**：没有权限访问所选模型
4. **代理设置问题**：需要配置代理才能访问国外模型

## 解决方案

### 方案 1：检查网络连接

确保你的网络可以正常访问国外网站，特别是 Anthropic 的 API 服务器。如果在中国大陆，可能需要使用 VPN 或代理。

### 方案 2：配置国内模型

如果无法访问国外模型，可以配置国内的大模型，如：

1. **创建配置文件**：在用户主目录下创建 `config/opencode` 文件夹，然后创建 `opencode.json` 文件

2. **配置国内模型**：例如配置基石智算的模型

```json
{
  "$schema": "https://opencode.ai/config.json",
  "provider": {
    "coreshub": {
      "npm": "@ai-sdk/openai-compatible",
      "name": "基石智算",
      "options": {
        "baseURL": "https://api.coreshub.cn/v1",
        "headers": {
          "Authorization": "Bearer 你的API密钥"
        }
      },
      "models": {
        "minimax/m2.1": {
          "name": "MiniMax-M2.1"
        },
        "glm-4.7": {
          "name": "GLM-4.7"
        }
      }
    }
  }
}
```

### 方案 3：使用内置模型

OpenCode 提供了一些内置模型，这些模型可能不需要额外的 API 密钥：

```powershell
# 列出所有可用模型
opencode models

# 使用特定模型
opencode run "Hello, how are you?" -m opencode/gpt-5-nano
```

### 方案 4：检查并更新 OpenCode CLI

确保你使用的是最新版本的 OpenCode CLI：

```powershell
# 检查版本
opencode --version

# 更新到最新版本
opencode upgrade
```

### 方案 5：重新安装 OpenCode CLI

如果上述方法都不奏效，可以尝试重新安装 OpenCode CLI：

```powershell
# 卸载
opencode uninstall

# 重新安装
npm install -g opencode-ai
```

## 调试方法

### 查看详细日志

使用 `--print-logs` 参数运行命令，查看详细日志以诊断问题：

```powershell
opencode run "Hello, how are you?" --print-logs
```

### 检查配置

查看当前配置，确保配置正确：

```powershell
opencode debug config
```

### 检查可用模型

确认 OpenCode CLI 可以正常列出可用模型：

```powershell
opencode models
```

## 常见问题及解决方案

### 问题 1：命令执行时间过长

**原因**：网络连接问题或模型响应缓慢

**解决方案**：
- 检查网络连接
- 使用国内模型
- 尝试使用轻量级模型

### 问题 2：无法访问 Anthropic 模型

**原因**：网络限制或 API 密钥问题

**解决方案**：
- 配置国内模型
- 使用内置模型
- 配置 VPN 或代理

### 问题 3：配置文件错误

**原因**：配置文件格式不正确

**解决方案**：
- 检查配置文件的 JSON 格式
- 确保 API 密钥正确
- 参考官方文档创建正确的配置文件

## 参考资源

- [OpenCode 官方文档](https://opencode.ai)
- [基石智算 API 文档](https://docs.coreshub.cn)
- [技术爬爬虾 B 站视频教程]

## 总结

OpenCode CLI 不回答问题的主要原因是网络连接问题或模型配置问题。通过配置国内模型、检查网络连接或使用内置模型，大多数情况下可以解决这个问题。如果问题仍然存在，建议查看详细日志以获取更多诊断信息。