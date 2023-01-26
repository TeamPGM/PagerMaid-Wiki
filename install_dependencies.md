# 安装软件包依赖

## Arch Linux

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

## Git

?> 此软件包用于拉取 PagerMaid 仓库及用于 PagerMaid 的后续更新。

```bash
sudo pacman -S git
```

## Debian / Ubuntu

### neofetch

?> 此软件包用于显示系统信息，如您没有显示系统信息需求，您可以无需安装此软件包。

```bash
sudo apt install neofetch -y
```

### zbar

?> 此软件包用于处理二维码信息，如您没有处理二维码信息需求，您可以无需安装此软件包。

```bash
sudo apt install libzbar-dev -y
```

### Pip

?> 此软件包为必须依赖包，用于安装 Python 依赖。

```bash
sudo apt install python3-pip -y
```

### Git

?> 此软件包用于拉取 PagerMaid 仓库及用于 PagerMaid 的后续更新。

```bash
sudo apt install -y git
```

## CentOS 7

### neofetch

?> 此软件包用于显示系统信息，如您没有显示系统信息需求，您可以无需安装此软件包。

```bash
sudo yum install epel-release -y
curl -o /etc/yum.repos.d/konimex-neofetch-epel-7.repo https://copr.fedorainfracloud.org/coprs/konimex/neofetch/repo/epel-7/konimex-neofetch-epel-7.repo
sudo yum install neofetch -y
```

### zbar

?> 此软件包用于处理二维码信息，如您没有处理二维码信息需求，您可以无需安装此软件包。

```bash
sudo yum install zbar-devel -y
sudo yum install zbar -y
```

### Git

?> 此软件包用于拉取 PagerMaid 仓库及用于 PagerMaid 的后续更新。

```bash
sudo yum install -y git
```
