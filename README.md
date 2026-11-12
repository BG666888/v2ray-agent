# v2ray-agent (AI修改版)

[![License: AGPL v3](https://img.shields.io/badge/License-AGPL%20v3-blue.svg)](https://www.gnu.org/licenses/agpl-3.0)
[![Version: v3.5.42-pr1](https://img.shields.io/badge/Version-v3.5.42--pr1-green.svg)](https://github.com/BG666888/v2ray-agent)

基于 Bash 的 **Xray-core / sing-box** 多协议一体化管理脚本（基于 `mack-a/v2ray-agent` 进行深度重构、特性增强与交互净化）。

---

## 🚀 快速开始

### 一键安装 / 运行
在 root 权限的 Linux 服务器（Ubuntu / Debian / CentOS / Alpine）上执行：

```bash
wget -P /root -N --no-check-certificate "https://raw.githubusercontent.com/BG666888/v2ray-agent/master/install.sh" && chmod 700 /root/install.sh && /root/install.sh
```

### 快捷唤出
安装后终端输入以下命令即可秒开控制台：
```bash
vasma
```

---

## ⚡ 核心优化与增强特性

- **单屏 `0-9` 控制台与实时仪表盘**
  - 主菜单精简为三大分组（`0-9` 单屏直达，零滚屏），顶部实时渲染运行核心（支持 `Xray + sing-box` 双核指示）、Nginx 状态、TLS 证书剩余有效期及已安装协议端口。
- **黄金抗封锁 3 件套一键预设（菜单 `1 -> 1`）**
  - 支持基于 **Xray-core（推荐单核）** 或 **sing-box** 一键部署 `VLESS+Reality[Vision]`（TCP 443）+ `Hysteria2`（UDP 443）+ `VLESS+TCP[TLS_Vision]`（TCP 8443）组合，自动零冲突分配端口并跳过冗余交互。
- **节点健康自检面板（菜单 `6`）**
  - 一键输出 5 维体检报告：核心进程与 RSS 内存、BBR 拥塞控制与 IPv4/IPv6 出站、协议端口实际监听核验（`ss`/`lsof`）、TLS 证书期限与 Reality 伪装域名实时 `TLSv1.3 + ALPN h2` 握手探活（含耗时与 CDN 特征提示）、云安全组放行端口清单。
- **开箱即用的现代化订阅（菜单 `2`）**
  - **Clash / Mihomo**：节点直接内嵌，集成 `blackmatrix7` 规则源（11 万+ 国内域名白名单及 OpenAI、ClaudeAI、流媒体独立策略组）。
  - **sing-box**：采用现代化 `.srs` 二进制规则集，全面兼容新版客户端；内置 **0 DNS 泄露隐私防护**（`Fake-IP` + 海外 DoH 兜底 + `no-resolve` 严格隔离）。
  - 采用高对比度终端订阅卡片输出，信息清晰利落。
- **协议与端口集中管理（菜单 `3`）**
  - 收纳全协议端口修改（自动查重占、联动防火墙与 Port Hopping 迁移并刷新订阅）、**Reality 管理**（保留公私钥一键切换 `www.samsung.com` / `aws.amazon.com` 等优选 SNI）、**Hysteria2 / TUIC 端口跳跃**配置。
- **站点、证书与安全策略整合（菜单 `5`）**
  - 集成 SSL 证书续期/机构切换、Cloudflare CDN 优选节点、TLS ALPN 切换、伪装站点更换（10 款内置模板 / 302 跳转）、BT 封禁与域名黑名单管理。
- **双核管理、BBR 调优与无缓存同步（菜单 `7 / 8 / 9`）**
  - 支持 Xray / sing-box 核心升级、预览版与切换，保留 BBR 加速调优入口，并内置动态时间戳与 `--no-cache` 脚本/模板秒级同步更新。

---

## 📋 主菜单预览

```text
╭──────────────────────────────────────────────────────────────╮
│  v2ray-agent (AI修改版) - v3.5.42-pr1       快捷命令: vasma  │
╰──────────────────────────────────────────────────────────────╯
  运行核心 : Xray + sing-box [双核运行中]  |  Nginx: 运行中  |  证书: 剩余 85 天(有效)
  已装协议 : Reality+Vision(443) | Hysteria2(UDP:443) | VLESS+Vision(8443)
────────────────────────────────────────────────────────────────
  [部署与账号]
    1. 节点部署与重装  (黄金3件套 / 无域名Reality / 完整 / 自定义)
    2. 账号与订阅管理  (查看节点 / 订阅链接 / 多用户)

  [协议与网络]
    3. 协议与端口管理  (全协议改端口 / Reality SNI / Hy2跳跃 / TUIC)
    4. 智能分流与落地  (WARP / IPv6 / Socks5落地 / DNS)
    5. 站点与证书管理  (SSL证书 / CDN优选 / 伪装站 / 禁BT与黑名单)

  [运维与诊断]
    6. 节点健康自检    (端口实测 / BBR / 证书 / Reality SNI探活)
    7. 核心与日志管理  (Xray / sing-box 升级 / 切换核心 / 调试日志)
    8. BBR 与系统调优  (安装原版 BBR+FQ / Swap / DD 脚本)
    9. 脚本更新与卸载  (同步最新版 / 彻底清理)
────────────────────────────────────────────────────────────────
    0. 退出脚本
================================================================
```

### 二级菜单速查

| 主菜单 | 收纳功能 |
| :--- | :--- |
| **1. 节点部署与重装** | `1` 黄金抗封锁 3 件套预设 [推荐] · `2` 一键无域名安装 · `3` 完整/重新安装 · `4` 自定义组合安装 |
| **3. 协议与端口管理** | `1` 全协议端口修改 · `2` REALITY SNI/密钥管理 · `3` Hysteria2 端口跳跃 · `4` TUIC 协议管理 |
| **5. 站点与证书管理** | `1` SSL 证书管理 · `2` CDN 优选节点 · `3` 切换 TLS ALPN · `4` 更换伪装站 · `5` 禁 BT · `6` 域名黑名单 |
| **9. 脚本更新与卸载** | `1` 同步 GitHub 最新版 · `2` 彻底卸载清理 |

---

## 📄 许可证

本项目基于 [AGPL-3.0 许可证](LICENSE) 授权。
