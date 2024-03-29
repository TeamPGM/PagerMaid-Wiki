# 开始使用网页控制台

![](web/0.png)

## 说明

从 PGP 的 `1.3.0` 版本开始，我们支持通过网页控制台管理机器人的插件和一些设置，未来也会在控制台中添加更多功能。

网页控制台的默认地址为： [http://127.0.0.1:3333](http://127.0.0.1:3333)

## 功能

### 查看日志、重启、更新

![](web/1.png)

### 命令别名管理

![](web/2.png)

### 忽略群组管理

![](web/3.png)

### 本地插件管理

![](web/4.png)

### 插件仓库管理

![](web/5.png)

## 开启控制台

### 确认 host

如果你只需要内网访问，那么你将要配置的 `host` 为 `127.0.0.1`，如果你需要公网访问控制台，那么你将要配置的 `host` 为 `0.0.0.0`。

绝大多数情况，你的 `host` 为 `0.0.0.0`，请不要填入其他无关的值。

### 非 Docker 用户

请找到 PGP 的配置文件 `config.yml` ，此文件的默认路径为 `/var/lib/pagermaid/config.yml`，修改如下值

```yaml
web_interface:
  enable: "True"
  secret_key: "控制台密码"
  host: "0.0.0.0" // 或者上面你确认的 127.0.0.1 
  port: "3333"
  origins: ["*"]
```

### Docker 用户

由于 docker 需要进行端口映射，创建的旧容器无缝升级比较复杂，推荐使用新脚本进行重装，重装时将会询问是否开启 web 控制台
