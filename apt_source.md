# 第三方插件源

本功能旨在提供一种简便的方式方便开发者分发插件。

## 用户文档

第三方开发者会给你提供一个网址（插件源），例如 https://v2.xtaolabs.com ，你需要通过以下命令 添加/删除 此插件源

### 免责声明

这些插件源由第三方开发者制作和维护。作为应用提供者，TeamPGM 不对这些插件源的内容、准确性、安全性或可靠性负责。任何对插件源内容或使用结果产生的损失或损害，将与 PGP 无关。请您理解并自行承担使用这些插件源的风险。

建议您在安装和使用第三方插件源前谨慎评估第三方开发者的信誉。

### 安装

`apt_source add <第三方插件源网址>`

例如

`apt_source add https://v2.xtaolabs.com`

### 卸载

`apt_source del <第三方插件源网址>`

例如

`apt_source del https://v2.xtaolabs.com`

### 查看状态

`apt_source`

## 开发者文档

### 目录结构

.

├── 插件名称

│   ├── main.py // 插件文件

│   └── DES.md // 插件描述

└── list.json // 插件信息

### 插件信息文件结构

```json
{
  "list": [
    {
      "name": "插件名称",
      "version": "1.0", // 插件版本
      "section": "chat", // 插件分类
      "maintainer": "xtaodada", // 插件维护者
      "size": "1.0 kb", // 插件大小
      "supported": true, // 是否仍在维护
      "des_short": "", // 插件短描述
      "des": "" // 插件长描述
    }
  ]
}
```
