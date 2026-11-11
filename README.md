# v2ray-agent (AI修改版)

[![License: AGPL v3](https://img.shields.io/badge/License-AGPL%20v3-blue.svg)](https://www.gnu.org/licenses/agpl-3.0)
[![Version: v3.5.41-pr6](https://img.shields.io/badge/Version-v3.5.41--pr6-green.svg)](https://github.com/BG666888/v2ray-agent)

基于 Bash 的 **Xray-core / sing-box** 多协议一体化管理脚本（基于 `mack-a/v2ray-agent` 进行深度重构、BUG 修复与交互净化）。

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

## ⚡ 相比原版（mack-a）的核心优化与修复

| 优化维度 | 原版脚本 (mack-a) | 本版本 (AI修改版) |
| :--- | :--- | :--- |
| **Clash (Mihomo) 订阅** | 依赖外部 `proxy-providers` 导致**节点列表为空**；常报 `GEOSITE.dat` 丢失 | **节点直接内嵌**，全客户端即导即用；移除旧数据依赖，秒开秒连 |
| **路由分流准确率** | 旧版粗糙规则，国内网站经常误走代理 | 接入 **`blackmatrix7` 11 万+ 大陆域名白名单**，国内直连率 99.9% |
| **DNS 隐私防泄露** | 缺乏白名单隔离与 `no-resolve`，**严重泄漏国内 DNS** | **Fake-IP + `#DNS_Proxy` 海外 DoH + `no-resolve`**，实现 **0 DNS 泄露** |
| **sing-box 客户端兼容** | 残留已废弃的 `stack` 与 `type: "block"`，导致客户端崩溃报错 | 语法全量现代化迁移；升级 MetaCubeX binary `.srs` 规则与独立 Claude 分组 |
| **端口修改能力** | 只能添加新端口，无法修改已有协议端口 | 新增 **`8. 端口管理`**：一键改端口、自动查占用、联动防火墙并刷新订阅 |
| **Reality SNI 伪装** | 更换伪装域名必须全量重装，会重置公私钥导致客户端全断开 | 新增 **`5. REALITY 管理`**：**保留现有公私钥**一键更换域名 |
| **Hy2 端口跳跃** | 订阅 URI 直填端口段，导致 v2rayNG 等客户端测速 `-1` | 主端口连接 + `?mport=起始-结束` 标准参数，全客户端完美兼容 |
| **终端交互与订阅排版** | 选项跳跃、广告刷屏、几十行黑白大二维码严重污染终端 | **4 大分类（1-15 + 0返回）**，移除全部广告；**彻底剔除二维码**，采用清爽卡片展示 |
| **脚本更新机制** | 受 GitHub Raw 5分钟 CDN 缓存拖累，经常更新后“版本未生效” | 更新内置动态时间戳与 `--no-cache`，秒拉最新提交 |

---

## 📋 主菜单预览

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
