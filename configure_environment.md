# 配置环境

## 为 PagerMaid 创建用户

为了您的操作不当而造成不可预期的后果，应避免应用直接运行在 `root` 用户，此处我们为 PagerMaid 创建用户。

1. 创建用户

    创建 `pagermaid` 用户，并为其创建家目录：

    ```bash
    sudo useradd -m pagermaid
    ```

2. 设置密码（可选）

    如果您有需求为用户设置密码，只需执行 `sudo passwd pagermaid` 即可。

3. 为用户提供 `sudo` 权限（可选）

    如果您有需求让 PagerMaid 执行需要 `root` 权限的操作，则需进行以下操作：

    - 提供 `sudo` 权限

        ```bash
        sudo usermod -a -G sudo pagermaid
        ```

    - 使 pagermaid 用户无需密码认证使用 `sudo`

        在执行 `visudo` 后，在末尾追加以下内容：

        ```
        pagermaid ALL=(ALL) NOPASSWD:ALL
        ```

4. 设置默认 Shell（可选）

    默认情况下，创建用户后，用户的默认 Shell 为 `sh`，对用户的操作十分不便。
    
    通常情况下，我们选用 `bash` 作为我们的默认 Shell，当然，您也可以选用诸如 `zsh` 的 Shell。

    如果您有需求修改默认 Shell，则需进行以下操作：

    ```bash
    sudo chsh -s /bin/bash pagermaid
    ```

    （如果您不使用 `bash`，可以修改 `/bin/bash` 为你所需设置的 Shell 的路径）

5. 进入用户进行接下来的操作

    ```bash
    sudo su pagermaid       # 进入 pagermaid 用户
    cd ~                    # 进入 pagermaid 用户家目录
    ```
