# 安装并配置 PagerMaid

## 拉取项目

```bash
cd /var/lib
git clone https://github.com/TeamPGM/PagerMaid-Pyro.git pagermaid
cd pagermaid
```

## 安装依赖包

```bash
pip3 install -r requirements.txt
```

## 修改配置文件

1. 将配置 `config.gen.yml` 文件复制一份到 ./data/ 下，并且命名为 `config.yml`

    ```bash
    cp config.gen.yml ./data/config.yml   # 复制模板
    vi ./data/config.yml                  # 修改文件
    ```

2. 设置 API（可选）

    在 [Telegram 开发者面板](https://my.telegram.org/) 生成 API 信息，将 `App api_id` 和 `App api_hash` 分别填入 `api_key` 和 `api_hash`

3. 代理配置（可选）

    此步是将安装插件的获取源文件更改为国内可以访问的反代源。

    ```yaml
    git_source: "https://v2.xtaolabs.com/"
    ```

4. 二维码登录（用于无法接收到验证码）（可选）

    此步是将登录方式切换到手机扫码登录，解决无法收到验证码的问题，手机扫码途径：`运行 APP - 设置 - 设备 - 扫码登录新客户端`。

    ```yaml
    qrcode_login: "True"
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
WorkingDirectory=/var/lib/pagermaid
ExecStart=/usr/bin/python3 -m pagermaid
Restart=always
TEXT
```

## 常用指令

- 启动程序并设置为开机自启：`sudo systemctl enable --now pagermaid`
- 启动程序：`sudo systemctl start pagermaid`
- 停止程序：`sudo systemctl stop pagermaid`
- 重启程序：`sudo systemctl restart pagermaid`
- 查看运行状态：`sudo systemctl status pagermaid`
