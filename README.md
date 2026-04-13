# S-UI (中文脚本汉化版)
**An Advanced Web Panel • Built on SagerNet/Sing-Box**

![](https://img.shields.io/github/v/release/alireza0/s-ui.svg)
![S-UI Docker pull](https://img.shields.io/docker/pulls/alireza7/s-ui.svg)
[![Go Report Card](https://goreportcard.com/badge/github.com/alireza0/s-ui)](https://goreportcard.com/report/github.com/alireza0/s-ui)
[![Downloads](https://img.shields.io/github/downloads/alireza0/s-ui/total.svg)](https://img.shields.io/github/downloads/alireza0/s-ui/total.svg)
[![License](https://img.shields.io/badge/license-GPL%20V3-blue.svg?longCache=true)](https://www.gnu.org/licenses/gpl-3.0.en.html)

> **Disclaimer:** This project is only for personal learning and communication, please do not use it for illegal purposes, please do not use it in a production environment

**If you think this project is helpful to you, you may wish to give a**:star2:

**Want to contribute?** See [CONTRIBUTING.md](CONTRIBUTING.md) for development setup, coding conventions, testing, and the pull request process.

[!["Buy Me A Coffee"](https://www.buymeacoffee.com/assets/img/custom_images/orange_img.png)](https://www.buymeacoffee.com/alireza7)

<a href="https://nowpayments.io/donation/alireza7" target="_blank" rel="noreferrer noopener">
   <img src="https://nowpayments.io/images/embeds/donation-button-white.svg" alt="Crypto donation button by NOWPayments">
</a>

## Quick Overview
| Features                               |      Enable?       |
| -------------------------------------- | :----------------: |
| Multi-Protocol                         | :heavy_check_mark: |
| Multi-Language                         | :heavy_check_mark: |
| Multi-Client/Inbound                   | :heavy_check_mark: |
| Advanced Traffic Routing Interface     | :heavy_check_mark: |
| Client & Traffic & System Status       | :heavy_check_mark: |
| Subscription Link (link/json/clash + info)| :heavy_check_mark: |
| Dark/Light Theme                       | :heavy_check_mark: |
| API Interface                          | :heavy_check_mark: |
| Chinese Management Script               | :heavy_check_mark: |

## Supported Platforms
| Platform | Architecture | Status |
|----------|--------------|---------|
| Linux    | amd64, arm64, armv7, armv6, armv5, 386, s390x | ✅ Supported |
| Windows  | amd64, 386, arm64 | ✅ Supported |
| macOS    | amd64, arm64 | 🚧 Experimental |

## Screenshots

!["Main"](https://github.com/alireza0/s-ui-frontend/raw/main/media/main.png)

[Other UI Screenshots](https://github.com/alireza0/s-ui-frontend/blob/main/screenshots.md)

## API Documentation

[API-Documentation Wiki](https://github.com/alireza0/s-ui/wiki/API-Documentation)

## Default Installation Information
- Panel Port: 2095
- Panel Path: /app/
- Subscription Port: 2096
- Subscription Path: /sub/
- User/Password: admin

## 安装 (中文界面) ⚡ 推荐

```sh
bash <(curl -Ls https://raw.githubusercontent.com/2190297373/s-ui/main/install.sh)
```

> 此安装方式包含中文管理脚本，安装完成后运行 `s-ui` 即可看到中文菜单界面

### Linux/macOS (中文界面)
```sh
bash <(curl -Ls https://raw.githubusercontent.com/2190297373/s-ui/main/install.sh)
```

## 安装旧版本

如需安装特定版本（如降级），请在安装命令末尾添加版本号，例如 `1.0.0`：

```sh
VERSION=1.0.0 && bash <(curl -Ls https://raw.githubusercontent.com/2190297373/s-ui/main/install.sh) $VERSION
```

## Windows 安装 (英文界面)

1. 从 [GitHub Releases](https://github.com/alireza0/s-ui/releases/latest) 下载最新的 Windows 版本
2. 解压 ZIP 文件
3. 以管理员身份运行 `install-windows.bat`
4. 按照安装向导完成安装

## 手动安装

### Linux/macOS
1. 从 GitHub 下载最新版本的 S-UI: [https://github.com/alireza0/s-ui/releases/latest](https://github.com/alireza0/s-ui/releases/latest)
2. **可选** 下载中文版管理脚本: [https://raw.githubusercontent.com/2190297373/s-ui/main/s-ui.sh](https://raw.githubusercontent.com/2190297373/s-ui/main/s-ui.sh)
3. **可选** 将 `s-ui.sh` 复制到 `/usr/bin/` 并运行 `chmod +x /usr/bin/s-ui`
4. 将 s-ui tar.gz 文件解压到您选择的目录并导航到该目录
5. 将 *.service 文件复制到 `/etc/systemd/system/` 并运行 `systemctl daemon-reload`
6. 使用 `systemctl enable s-ui --now` 启用自启动并启动 S-UI 服务
7. 使用 `systemctl enable sing-box --now` 启动 sing-box 服务

### Windows (英文界面)
1. 从 GitHub 下载最新 Windows 版本: [https://github.com/alireza0/s-ui/releases/latest](https://github.com/alireza0/s-ui/releases/latest)
2. 下载对应的 Windows 安装包 (例如 `s-ui-windows-amd64.zip`)
3. 将 ZIP 文件解压到您选择的目录
4. 以管理员身份运行 `install-windows.bat`
5. 按照安装向导完成安装
6. 访问面板 http://localhost:2095/app

## 卸载 S-UI

```sh
sudo -i

systemctl disable s-ui  --now

rm -f /etc/systemd/system/sing-box.service
systemctl daemon-reload

rm -fr /usr/local/s-ui
rm /usr/bin/s-ui
```

## 使用 Docker 安装

<details>
   <summary>点击查看详情</summary>

### Usage

**Step 1:** Install Docker

```shell
curl -fsSL https://get.docker.com | sh
```

**Step 2:** Install S-UI

> Docker compose method

```shell
mkdir s-ui && cd s-ui
wget -q https://raw.githubusercontent.com/alireza0/s-ui/master/docker-compose.yml
docker compose up -d
```

> Use docker

```shell
mkdir s-ui && cd s-ui
docker run -itd \
    -p 2095:2095 -p 2096:2096 -p 443:443 -p 80:80 \
    -v $PWD/db/:/app/db/ \
    -v $PWD/cert/:/root/cert/ \
    --name s-ui --restart=unless-stopped \
    alireza7/s-ui:latest
```

> Build your own image

```shell
git clone https://github.com/alireza0/s-ui
git submodule update --init --recursive
docker build -t s-ui .
```

</details>

## Manual run ( contribution )

<details>
   <summary>Click for details</summary>

### Build and run whole project
```shell
./runSUI.sh
```

### Clone the repository
```shell
# clone repository
git clone https://github.com/alireza0/s-ui
# clone submodules
git submodule update --init --recursive
```


### - Frontend

Visit [s-ui-frontend](https://github.com/alireza0/s-ui-frontend) for frontend code

### - Backend
> Please build frontend once before!

To build backend:
```shell
# remove old frontend compiled files
rm -fr web/html/*
# apply new frontend compiled files
cp -R frontend/dist/ web/html/
# build
go build -o sui main.go
```

To run backend (from root folder of repository):
```shell
./sui
```

</details>

## Languages

- English
- Farsi
- Vietnamese
- Chinese (Simplified)
- Chinese (Traditional)
- Russian

## Features

- Supported protocols:
  - General:  Mixed, SOCKS, HTTP, HTTPS, Direct, Redirect, TProxy
  - V2Ray based: VLESS, VMess, Trojan, Shadowsocks
  - Other protocols: ShadowTLS, Hysteria, Hysteria2, Naive, TUIC
- Supports XTLS protocols
- An advanced interface for routing traffic, incorporating PROXY Protocol, External, and Transparent Proxy, SSL Certificate, and Port
- An advanced interface for inbound and outbound configuration
- Clients’ traffic cap and expiration date
- Displays online clients, inbounds and outbounds with traffic statistics, and system status monitoring
- Subscription service with ability to add external links and subscription
- HTTPS for secure access to the web panel and subscription service (self-provided domain + SSL certificate)
- Dark/Light theme

## 中文管理脚本 (s-ui.sh)

本项目提供中文界面的管理脚本 `s-ui.sh`，方便中文用户管理 S-UI 面板。

### 功能特性

| 编号 | 功能 | 说明 |
|------|------|------|
| 0 | 退出 | 退出管理菜单 |
| 1 | 安装 | 安装 s-ui (全新安装) |
| 2 | 更新 | 更新 s-ui 到最新版本 |
| 3 | 自定义版本 | 安装特定版本 (例如降级) |
| 4 | 卸载 | 完全卸载 s-ui |
| 5 | 重置管理员凭据为默认 | 忘记密码时使用，恢复默认账号密码 |
| 6 | 设置管理员凭据 | 修改面板登录的账号和密码 |
| 7 | 查看管理员凭据 | 查看当前的账号密码 |
| 8 | 重置面板设置 | 将面板设置恢复出厂 |
| 9 | 设置面板设置 | 修改面板端口、路径等 |
| 10 | 查看面板设置 | 查看当前面板配置信息 |
| 11 | 启动 s-ui | 启动服务 |
| 12 | 停止 s-ui | 停止服务 |
| 13 | 重启 s-ui | 重启服务 (配置修改后常用) |
| 14 | 检查状态 | 查看服务是否运行正常 |
| 15 | 查看日志 | 查看运行日志 (排错用) |
| 16 | 开启开机自启 | 设置随系统启动 |
| 17 | 关闭开机自启 | 取消随系统启动 |
| 18 | 开启/关闭 BBR | 优化网络拥堵控制算法 |
| 19 | SSL 证书管理 | 申请 Let's Encrypt 证书 (HTTP 验证) |
| 20 | Cloudflare SSL 证书 | 申请 Cloudflare 证书 (DNS 验证) |

### 使用方法

```bash
# 安装后自动获得中文管理脚本
# 或手动下载
wget -O /usr/bin/s-ui https://raw.githubusercontent.com/2190297373/s-ui/main/s-ui.sh
chmod +x /usr/bin/s-ui

# 运行管理脚本
s-ui

# 命令行模式 (无需交互)
s-ui start      # 启动
s-ui stop       # 停止
s-ui restart    # 重启
s-ui status     # 查看状态
s-ui enable     # 开启开机自启
s-ui disable    # 关闭开机自启
s-ui log        # 查看日志
s-ui update     # 更新
s-ui uninstall  # 卸载
```

### 界面预览

```
  S-UI 管理脚本
————————————————————————————
  0. 退出
————————————————————————————
  1. 安装
  2. 更新
  3. 自定义版本
  4. 卸载
————————————————————————————
  5. 重置管理员凭据为默认
  6. 设置管理员凭据
  7. 查看管理员凭据
...
```

## Environment Variables

<details>
  <summary>Click for details</summary>

### Usage

| Variable       |                      Type                      | Default       |
| -------------- | :--------------------------------------------: | :------------ |
| SUI_LOG_LEVEL  | `"debug"` \| `"info"` \| `"warn"` \| `"error"` | `"info"`      |
| SUI_DEBUG      |                   `boolean`                    | `false`       |
| SUI_BIN_FOLDER |                    `string`                    | `"bin"`       |
| SUI_DB_FOLDER  |                    `string`                    | `"db"`        |
| SINGBOX_API    |                    `string`                    | -             |

</details>

## SSL Certificate

<details>
  <summary>Click for details</summary>

### Certbot

```bash
snap install core; snap refresh core
snap install --classic certbot
ln -s /snap/bin/certbot /usr/bin/certbot

certbot certonly --standalone --register-unsafely-without-email --non-interactive --agree-tos -d <Your Domain Name>
```

</details>

## Stargazers over Time
[![Stargazers over time](https://starchart.cc/alireza0/s-ui.svg)](https://starchart.cc/alireza0/s-ui)
