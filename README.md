# dsh-archive-button

[English](README.en.md) · 中文

![归档按钮与重启按钮（含两击确认态）界面示意](assets/dsh-archive-button-restart-button.png)

*界面示意：按官方主题变量渲染的版式，非实机截图。*

侧栏工作区标题行上的归档按钮（工作区标题行没挂载时回落到 footer 胶囊）。第一次点先空跑扫描，列出空闲超过 3 天的会话；第二次点把每个会话打包成逐字节校验的 zip，并删掉原目录。host 半端注册 `/dsh-archive/*` 路由并调归档脚本，client 半端只画按钮。模型不会触发它。

## 装

```sh
dsh plugin --profile web add file:<本仓库>
```

装完重启 web 实例。

## 环境变量

| 变量 | 默认 | 说明 |
|---|---|---|
| `DSH_ROOT` | `~/DeepSeek_harness` | DSH 安装根；归档脚本、归档目录、按钮日志都由它派生 |

## 前提

- Windows PowerShell 5.1
- `<DSH_ROOT>\scripts\archive-dsh-sessions.ps1` 需自备，本仓库不含该脚本
