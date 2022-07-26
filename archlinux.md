﻿# Archlinux

一个经典的国内家用 Linux 。 

# 拉取项目

本项目托管在 `github` ，所以您首先需要检查您是否已经安装 `git` 软件包。并且我们发现当 `git` 软件包版本过低时，无法实现程序的自动更新，所以您需要首先升级 `git` 软件包：

```bash
sudo pacman -S git
```

从仓库拉取项目

```bash
cd /var/lib && git clone https://github.com/TeamPGM/PagerMaid-Pyro.git pagermaid && cd pagermaid
```

# 安装软件包

## neofetch

?> 此软件包用于显示系统信息，如您没有显示系统信息需求，您可以无需安装此软件包。

```bash
sudo pacman -S neofetch
```

## zbar

?> 此软件包用于处理二维码信息，如您没有处理二维码信息需求，您可以无需安装此软件包。

```bash
sudo pacman -S zbar
```

# 安装依赖包

```bash
pip3 install -r requirements.txt
```

# 修改配置文件

将配置 `config.gen.yml` 文件复制一份并且命名为 `config.yml`

```bash
cp config.gen.yml config.yml
```

然后去 [telegram 官网](https://my.telegram.org/) 生成 api 填入配置文件内，我们只需要复制 `api id` 和 `api_hash` 值 填入 `api_key` 和 `api_hash` 。

```bash
vi config.yml
```

> 按 i 进入编辑模式，粘贴好后，按下 esc 输入 shift 加冒号，输入 wq 保存退出

## 代理配置

### GitSource

此步是将安装插件的获取源文件更改为国内可以访问的反代源，但是可能因为 cdn 原因，插件更新不及时。

```bash
git_source: "https://gitlab.com/Xtao-Labs/PagerMaid_Plugins/-/raw/master/"
```

# 登录账号

```bash
python3 -m pagermaid
```

此步需要填入完整的电话号码（eg：`+12569986522`）然后 tg 会发给你的其他客户端发送验证码，填入验证码后，回车，如有两步验证密码，则再输入两步验证密码即可。

停止运行：

```bash
ctrl + c
```

!> 请注意保护好您已登录的 `pagermaid.session` 。此文件可以进行账号所有操作，请不要分享给他人使用。

# 进程守护

此步骤可以方便 `pagermaid` 的自动运行，您无需在 `pagermaid` 意外退出后重新登录主机进行操作。

```bash
cat <<'TEXT' > /etc/systemd/system/pagermaid.service
[Unit]
Description=PagerMaid-Pyro telegram utility daemon
After=network.target

[Install]
WantedBy=multi-user.target

[Service]
Type=simple
WorkingDirectory=/var/lib/pagermaid
ExecStart=/usr/bin/python3 -m pagermaid
Restart=always
TEXT
```

# 常用指令

启动程序：`systemctl start pagermaid`

设置为开机自启：`systemctl enable pagermaid`

停止程序：`systemctl stop pagermaid`
