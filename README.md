# v2ray-agent (AI修改版)

[![License: AGPL v3](https://img.shields.io/badge/License-AGPL%20v3-blue.svg)](https://www.gnu.org/licenses/agpl-3.0)

基于 Bash 的 **Xray-core / sing-box** 多协议安装与管理脚本（Fork 自 `mack-a/v2ray-agent` 并由 AI 深度修改优化）。

---

## ✨ AI修改版核心增强特性

1. **全新精炼交互界面与极简订阅输出**：
   - 重构主菜单为 **`[安装与部署]`**、**`[节点与协议]`**、**`[分流与站点]`**、**`[核心与系统]`** 四大板块（连续编号 `1-15`，支持 `0` 随时返回/退出）。
   - 彻底移除冗余且无实效的终端订阅二维码及第三方在线二维码生成链接，采用高对比度现代卡片式订阅展示，清晰直观。
   - 快捷呼出命令全面支持 **`vasma`** 与 **`vasgm`**。
2. **全协议端口一键管理（`8. 端口管理`）**：
   - 自动识别已安装的 VLESS (TCP/Reality Vision/gRPC/XHTTP)、Trojan、Hysteria2、TUIC 及 Nginx 订阅服务端口。
   - 修改端口后自动检测端口占用、更新配置、放行防火墙、联动迁移 Hysteria2/TUIC 端口跳跃规则并静默刷新客户端订阅。
3. **Reality 伪装域名 (SNI) 快捷更换（`5. REALITY 管理`）**：
   - 支持保留现有公私钥直接更换伪装域名（内置 5 个高可用优选域名一键选择，或输入任意自定义域名）。
   - 自动同步更新 Xray（Vision / gRPC / XHTTP）与 sing-box 配置并刷新订阅。
4. **Clash.Meta (Mihomo / FlClash) 权威规则集成与 0 泄露 DNS 架构**：
   - 全面引入 **`blackmatrix7/ios_rule_script`** 顶级活跃规则源（涵盖 11 万+ 国内域名大白名单及专用 OpenAI、ClaudeAI、流媒体策略组）。
   - 采用 `fake-ip` + `respect-rules` + `#DNS_Proxy` 海外加密 DoH 兜底解析，严格限定国内白名单才派发国内 DNS，所有 IP 匹配均强制 `no-resolve`，彻底消灭 DNS 泄露。
5. **sing-box 客户端规则全面同步升级**：
   - 升级采用 MetaCubeX 官方 binary `.srs` 高速规则集，同步划分独立 **`ClaudeAI`**、**`OpenAI`**、**`Telegram`**、**`YouTube`** 等专用策略组。
   - 优化 DNS 路由层级，默认未知解析强制走代理海外 DoH，彻底杜绝 sing-box 客户端 DNS 泄露风险。
6. **Hysteria2 端口跳跃全客户端兼容**：
   - 标准 URI 使用主监听端口作为连接地址，通过 `?mport=起始-结束` 传递跳跃端口范围，解决 v2rayNG 等客户端开启端口跳跃后测速 `-1` 的问题。
7. **更新防缓存机制**：
   - 脚本更新与模板分发自带 `--no-cache` 与动态时间戳参数，彻底避免 GitHub Raw CDN 5 分钟缓存导致的“版本未生效”现象。

---

## 🚀 快速开始

### 1. 一键安装 / 运行脚本

在拥有 `root` 权限的 Linux 服务器（Ubuntu / Debian / CentOS / Alpine）上执行：

```bash
wget -P /root -N --no-check-certificate "https://raw.githubusercontent.com/BG666888/v2ray-agent/master/install.sh" && chmod 700 /root/install.sh && /root/install.sh
```

### 2. 日常呼出管理菜单

安装完成后，在终端任意位置输入以下任一快捷命令即可打开管理菜单：

```bash
vasma
# 或
vasgm
```

---

## 📋 主菜单功能速览

```text
================================================================
  当前版本：v3.5.41-pr6  (AI修改版)
  开源仓库：BG666888/v2ray-agent   |   快捷命令：vasma / vasgm
  运行核心 : Xray-core [运行中]
  已装协议 : VLESS+Reality[Vision] | Hysteria2
================================================================
  [安装与部署]
    1. 重新完整安装   (带域名全套协议)
    2. 任意组合安装   (按需自定义协议)
    3. 一键无域名安装 (Reality 免域名极速部署)
  [节点与协议]
    4. 账号与订阅管理 (查看节点 / 订阅链接 / 多用户)
    5. REALITY 管理   (一键更换伪装域名 SNI / 重置)
    6. Hysteria2 管理 (端口跳跃配置 / 状态查看)
    7. TUIC 协议管理  (安装 / 卸载 / 端口跳跃)
    8. 端口管理       (全协议端口修改 / 防火墙联动)
  [分流与站点]
    9. 智能分流工具   (WARP / IPv6 / Socks5落地 / DNS)
   10. 证书与 CDN     (SSL 证书续期 / CDN 优选节点)
   11. 伪装站与安全   (更换伪装网站 / 禁 BT / 黑名单)
  [核心与系统]
   12. 核心服务管理   (Xray / sing-box 升级 / 预览版 / 日志)
   13. BBR 与系统工具 (安装 BBR 加速 / Swap / DD 系统)
   14. 更新管理脚本   (从 GitHub 同步最新版本)
   15. 卸载管理脚本   (彻底清理所有服务与配置)
----------------------------------------------------------------
    0. 退出脚本
================================================================
```

---

## 📄 许可证

本项目基于 [AGPL-3.0 许可证](LICENSE) 授权。
