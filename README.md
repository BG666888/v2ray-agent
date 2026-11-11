# v2ray-agent (定制增强版)

[![License: AGPL v3](https://img.shields.io/badge/License-AGPL%20v3-blue.svg)](https://www.gnu.org/licenses/agpl-3.0)

基于 Bash 的 **Xray-core / sing-box** 多协议安装与管理脚本（Fork 自 `mack-a/v2ray-agent` 并进行深度定制优化）。

---

## ✨ 定制版核心增强特性

1. **全新精简交互界面**：
   - 重构主菜单为 **`[安装与部署]`**、**`[节点与协议]`**、**`[分流与站点]`**、**`[核心与系统]`** 四大板块（连续编号 `1-15`，支持 `0` 随时返回/退出）。
   - 顶部实时状态面板显示核心运行状态与已装协议列表，移除冗余推广信息与英文版脚本。
2. **全协议端口一键管理（`8. 端口管理`）**：
   - 自动识别已安装的 VLESS (TCP/Reality Vision/gRPC/XHTTP)、Trojan、Hysteria2、TUIC 及 Nginx 订阅服务端口。
   - 修改端口后自动检测端口占用、更新配置、放行防火墙、联动迁移 Hysteria2/TUIC 端口跳跃规则并静默刷新客户端订阅。
3. **Reality 伪装域名 (SNI) 快捷更换（`5. REALITY 管理`）**：
   - 支持保留现有公私钥直接更换伪装域名（内置 5 个高可用优选域名一键选择，或输入任意自定义域名）。
   - 自动同步更新 Xray（Vision / gRPC / XHTTP）与 sing-box 配置并刷新订阅。
4. **sing-box 预览版支持与 `1.12 ~ 1.15` 规则兼容（`12. 核心服务管理`）**：
   - 支持一键升级 sing-box 最新正式版（Stable）或预览版（Pre-release，如 `1.15.x`）。
   - 自动迁移废弃的 `type: "block"` 出站为现代 `action: "reject"` 动作，清理客户端 TUN 废弃的 `stack` 字段，完美兼容 sing-box `1.12 ~ 1.15` 客户端。
5. **Clash.Meta (Mihomo / FlClash) 深度轻量化与防 DNS 泄露**：
   - 移除 20+ 个外部 `rule-providers` 规则集依赖，全面改用 Mihomo / FlClash 原生内置 `GEOSITE` / `GEOIP` 引擎，秒开秒连。
   - 启用 `fake-ip` + `respect-rules` + `nameserver-policy`，国内域名直连解析，海外域名强制通过 `#DNS_Proxy` 代理隧道解析，所有 IP 规则附带 `no-resolve`，彻底杜绝 DNS 泄露。
6. **Hysteria2 端口跳跃全客户端兼容**：
   - 标准 URI 使用主监听端口作为连接地址，通过 `?mport=起始-结束` 传递跳跃端口范围，解决 v2rayNG 等客户端开启端口跳跃后测速 `-1` 的问题。

---

## 🚀 快速开始

### 1. 一键安装 / 运行脚本

在拥有 `root` 权限的 Linux 服务器（Ubuntu / Debian / CentOS / Alpine）上执行：

```bash
wget -P /root -N --no-check-certificate "https://raw.githubusercontent.com/BG666888/v2ray-agent/master/install.sh" && chmod 700 /root/install.sh && /root/install.sh
```

### 2. 日常呼出管理菜单

安装完成后，在终端任意位置输入以下快捷命令即可打开管理菜单：

```bash
vasma
```

### 3. Docker Reality 独立部署版（可选）

```bash
wget -P /root -N --no-check-certificate "https://raw.githubusercontent.com/BG666888/v2ray-agent/master/shell/docker_reality.sh" && chmod 700 /root/docker_reality.sh && /root/docker_reality.sh
```
Docker 版日常管理快捷命令：`vasmad`

---

## 📋 主菜单功能速览

```text
================================================================
  当前版本：v3.5.41-pr2
  项目仓库：BG666888/v2ray-agent  |  快捷命令：vasma
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
