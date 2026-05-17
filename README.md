# zuma-desktop-agent

ZumaRobot Windows 桌面自动化机器人 SKILL 端代理工具。

支持自动化发布小红书笔记、抖音、X/推特等，支持 AI 动态生成配图，一句话完成所有操作。

## 快速安装（推荐）

### 找到你的 Skills 目录

不同 OpenClaw 发行版的 skills 目录位置可能不同：

| 发行版 | 默认 Skills 目录 |
|--------|-----------------|
| QClaw | `~/.qclaw/skills/` |
| OpenClaw | `~/.openclaw/skills/` |
| ArkClaw | `~/.arkclaw/skills/` |

**确认方法**：查看你的 OpenClaw 配置文件中 `skills.directories` 或 `skills.entries` 所在位置。

### 方式一：一键安装脚本（自动启用）

在 PowerShell 中执行（根据你的实际路径修改 `$skillDir`）：

```powershell
# 1. 设置你的 skills 目录（根据你的发行版修改）
$skillDir = "$env:USERPROFILE\.qclaw\skills\zuma-desktop-agent"  # QClaw 用户
# $skillDir = "$env:USERPROFILE\.openclaw\skills\zuma-desktop-agent"  # OpenClaw 用户
# $skillDir = "$env:USERPROFILE\.akrclaw\skills\zuma-desktop-agent"  # AkrClaw 用户

# 2. 克隆到 skills 目录
git clone https://github.com/biglobin/zuma-desktop-agent.git $skillDir

# 3. 安装依赖
Set-Location $skillDir
npm install

# 4. 启用技能（关键步骤！）
# 请使用你的 OpenClaw 的 gateway.config.patch 工具设置：
# "zuma-desktop-agent": { "enabled": true }
# 然后重启 Gateway

# 5. 验证是否启用
# 检查配置中 skills.entries.zuma-desktop-agent.enabled 是否为 true
```

### 方式二：手动安装

1. 将 `zuma-desktop-agent/` 目录放到 **你的 skills 目录** 下
2. 进入目录执行 `npm install`
3. **【必须】在 OpenClaw 配置中启用技能：**
   - 使用你的发行版对应的配置工具（如 `qclaw gateway config.patch`、`openclaw gateway config.patch` 或 Web UI）
   - 添加 `"zuma-desktop-agent": { "enabled": true }`
   - 重启 Gateway（如 `qclaw gateway restart`）
4. 验证：使用对应命令确认 `skills.entries.zuma-desktop-agent.enabled` 为 `true`

## 常见问题

**Q: 安装后技能没有响应？**
A: 99% 是因为没有执行第3步——在配置中启用技能。文件放到目录下≠自动启用，必须显式设置 `enabled: true`。

## 依赖

- Node.js 18+
- ZumaRobot.exe（路径：`D:\ZUMA\ZUMAROBOT\ZumaRobot.exe`）

## 项目地址

- GitHub: https://github.com/biglobin/zuma-desktop-agent
- Gitee: https://gitee.com/biglobin/zuma_desktop_agent
