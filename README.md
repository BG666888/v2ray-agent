# v2ray-agent (AI修改版)

[![License: AGPL v3](https://img.shields.io/badge/License-AGPL%20v3-blue.svg)](https://www.gnu.org/licenses/agpl-3.0)
[![Version: v3.5.41-pr7](https://img.shields.io/badge/Version-v3.5.41--pr7-green.svg)](https://github.com/BG666888/v2ray-agent)

基于 Bash 的 **Xray-core / sing-box** 多协议一体化管理脚本（基于 `mack-a/v2ray-agent` 进行深度重构、特性增强与交互净化）。

---

## 🚀 快速开始

### 一键安装 / 运行
在 root 权限的 Linux 服务器（Ubuntu / Debian / CentOS / Alpine）上执行：

```bash
wget -P /root -N --no-check-certificate "https://raw.githubusercontent.com/BG666888/v2ray-agent/master/install.sh" && chmod 700 /root/install.sh && /root/install.sh
```

### 快捷唤出
安装后终端输入以下任一命令即可秒开控制台：
```bash
vasma
# 或
vasgm
```

---

## ⚡ 核心优化与增强特性

- **开箱即用的现代化订阅**
  - **Clash / Mihomo**：节点直接内嵌，完美集成 `blackmatrix7` 权威规则源（11万+ 国内域名白名单与独立 OpenAI、ClaudeAI、流媒体策略组），即导即用。
  - **sing-box**：采用现代化 `.srs` 二进制规则集，分流精准迅速，全面兼容最新客户端。
- **0 DNS 泄露隐私防护**
  - 采用 `Fake-IP` + 海外加密 DoH 代理兜底 + `no-resolve` 严格白名单隔离，彻底杜绝 DNS 泄露。
- **全协议端口灵活管理（菜单 8）**
  - 支持直接修改已安装的任意协议端口，自动排查端口占用、联动放行防火墙并同步刷新客户端订阅。
- **Reality 伪装快捷更换（菜单 5）**
  - 支持在保留现有公私钥的情况下直接更换伪装域名（SNI），内置高可用优选列表，客户端免重新配置。
- **Hysteria2 / TUIC 端口跳跃优化**
  - 采用标准化参数传递端口跳跃范围，完美兼容各大主流客户端测速与稳定连接。
- **清爽现代的交互体验**
  - 规范四大功能板块分类（连续编号 `1-15`，`0` 返回/退出），支持 `vasma` / `vasgm` 极速呼出。
  - 彻底剔除冗长黑白终端二维码，采用高对比度现代订阅卡片，信息清晰利落。
- **极速无缓存更新机制**
  - 脚本与模板更新内置动态时间戳与 `--no-cache` 防缓存机制，确保秒级同步最新提交。

---

## 📋 主菜单预览

```text
================================================================
  当前版本：v3.5.41-pr7  (AI修改版)
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
