# 安装并配置 PagerMaid

## 拉取项目

```bash
git clone https://github.com/TeamPGM/PagerMaid-Pyro.git pagermaid
```

## 安装依赖包

```bash
pip3 install -r requirements.txt
```

## 修改配置文件

1. 将配置 `config.gen.yml` 文件复制一份并且命名为 `config.yml`

    ```bash
    cp config.gen.yml config.yml        # 复制模板
    vi config.yml                       # 修改文件
    ```

2. 设置 API

    在 [Telegram 用户管理面板](https://my.telegram.org/) 生成 API 信息，将 `App api_id` 和 `App api_hash` 分别填入 `api_key` 和 `api_hash`

3. 代理配置（可选）

    此步是将安装插件的获取源文件更改为国内可以访问的反代源，但是可能因为 cdn 原因，插件更新不及时。

    ```yaml
    git_source: "https://gitlab.com/Xtao-Labs/PagerMaid_Plugins/-/raw/master/"
    ```

## 登录账号

```bash
python3 -m pagermaid
```

填入完整的电话号码（如：`+12569986522`），随即 Telegram 将会向你的其他客户端发送验证码，填入验证码即可。如有两步验证密码，则再输入两步验证密码即可。

完成以上步骤后，按下 `Ctrl + C` 终止应用。

!> 请注意保护好您已登录的 `pagermaid.session` 。此文件可以进行账号所有操作，请不要分享给他人使用。

## 进程守护

此步骤可以方便 `PagerMaid` 的自动运行，您无需在 `PagerMaid` 意外退出或主机重启后重新登录主机进行操作。

```bash
sudo cat <<'TEXT' > /etc/systemd/system/pagermaid.service
[Unit]
Description=PagerMaid-Pyro Telegram Utility Daemon
After=network.target

[Install]
WantedBy=multi-user.target

[Service]
Type=simple
User=pagermaid
Group=pagermaid
WorkingDirectory=/home/pagermaid/pagermaid
ExecStart=/usr/bin/python3 -m pagermaid
Restart=always
TEXT
```

## 常用指令

- 启动程序：`sudo systemctl start pagermaid`
- 设置为开机自启：`sudo systemctl enable pagermaid`
- 停止程序：`sudo systemctl stop pagermaid`
