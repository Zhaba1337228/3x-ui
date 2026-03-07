[English](/README.md) | [فارسی](/README.fa_IR.md) | [العربية](/README.ar_EG.md) |  [中文](/README.zh_CN.md) | [Español](/README.es_ES.md) | [Русский](/README.ru_RU.md)

<p align="center">
  <picture>
    <source media="(prefers-color-scheme: dark)" srcset="./media/3x-ui-dark.png">
    <img alt="3x-ui" src="./media/3x-ui-light.png">
  </picture>
</p>

[![Release](https://img.shields.io/github/v/release/mhsanaei/3x-ui.svg)](https://github.com/MHSanaei/3x-ui/releases)
[![Build](https://img.shields.io/github/actions/workflow/status/mhsanaei/3x-ui/release.yml.svg)](https://github.com/MHSanaei/3x-ui/actions)
[![GO Version](https://img.shields.io/github/go-mod/go-version/mhsanaei/3x-ui.svg)](#)
[![Downloads](https://img.shields.io/github/downloads/mhsanaei/3x-ui/total.svg)](https://github.com/MHSanaei/3x-ui/releases/latest)
[![License](https://img.shields.io/badge/license-GPL%20V3-blue.svg?longCache=true)](https://www.gnu.org/licenses/gpl-3.0.en.html)
[![Go Reference](https://pkg.go.dev/badge/github.com/mhsanaei/3x-ui/v2.svg)](https://pkg.go.dev/github.com/mhsanaei/3x-ui/v2)
[![Go Report Card](https://goreportcard.com/badge/github.com/mhsanaei/3x-ui/v2)](https://goreportcard.com/report/github.com/mhsanaei/3x-ui/v2)

**3X-UI** — advanced, open-source web-based control panel designed for managing Xray-core server. It offers a user-friendly interface for configuring and monitoring various VPN and proxy protocols.

> [!IMPORTANT]
> This project is only for personal usage, please do not use it for illegal purposes, and please do not use it in a production environment.

As an enhanced fork of the original X-UI project, 3X-UI provides improved stability, broader protocol support, and additional features.

## Quick Start

```bash
bash <(curl -Ls https://raw.githubusercontent.com/Zhaba1337228/3x-ui-PostgreSQL/master/install.sh)
```

For full documentation, please visit the [project Wiki](https://github.com/MHSanaei/3x-ui/wiki).

## PostgreSQL Setup

The panel now supports both `sqlite` and `postgres`.

### Systemd install

The packaged systemd units already load environment files:

- Debian/Ubuntu: `/etc/default/x-ui`
- RHEL/CentOS/Alma/Rocky: `/etc/sysconfig/x-ui`

Example:

```bash
cat >/etc/default/x-ui <<'EOF'
XRAY_VMESS_AEAD_FORCED=false
XUI_DB_DRIVER=postgres
XUI_POSTGRES_DSN=host=127.0.0.1 port=5432 user=xui password=change_me dbname=xui sslmode=disable TimeZone=UTC
XUI_DB_MAX_IDLE_CONNS=10
XUI_DB_MAX_OPEN_CONNS=50
EOF

systemctl daemon-reload
systemctl restart x-ui
systemctl status x-ui
```

Minimal PostgreSQL bootstrap on the server:

```bash
sudo -u postgres psql <<'SQL'
CREATE USER xui WITH PASSWORD 'change_me';
CREATE DATABASE xui OWNER xui;
SQL
```

### Docker Compose install

1. Copy `.env.example` to `.env`
2. Set:
   - `XUI_DB_DRIVER=postgres`
   - `XUI_POSTGRES_DSN=host=127.0.0.1 port=5432 user=xui password=change_me dbname=xui sslmode=disable TimeZone=UTC`
3. Start Postgres profile and panel:

```bash
docker compose --profile postgres up -d --build
```

If you keep `XUI_DB_DRIVER=sqlite`, Postgres is not required and the panel continues using the local DB file.

## A Special Thanks to

- [alireza0](https://github.com/alireza0/)

## Acknowledgment

- [Iran v2ray rules](https://github.com/chocolate4u/Iran-v2ray-rules) (License: **GPL-3.0**): _Enhanced v2ray/xray and v2ray/xray-clients routing rules with built-in Iranian domains and a focus on security and adblocking._
- [Russia v2ray rules](https://github.com/runetfreedom/russia-v2ray-rules-dat) (License: **GPL-3.0**): _This repository contains automatically updated V2Ray routing rules based on data on blocked domains and addresses in Russia._

## Support project

**If this project is helpful to you, you may wish to give it a**:star2:

<a href="https://www.buymeacoffee.com/MHSanaei" target="_blank">
<img src="./media/default-yellow.png" alt="Buy Me A Coffee" style="height: 70px !important;width: 277px !important;" >
</a>

</br>
<a href="https://nowpayments.io/donation/hsanaei" target="_blank" rel="noreferrer noopener">
   <img src="./media/donation-button-black.svg" alt="Crypto donation button by NOWPayments">
</a>

## Stargazers over Time

[![Stargazers over time](https://starchart.cc/MHSanaei/3x-ui.svg?variant=adaptive)](https://starchart.cc/MHSanaei/3x-ui)
