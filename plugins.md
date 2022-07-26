# 插件入门

## 插件结构

在编写插件之前，首先我们需要了解一下插件的概念。

在 PGP 中，插件是一个单独的 Python 文件 file。
PGP 会在加载时对这些文件做一些特殊的处理使得他们成为一个插件。

## 创建插件

在 `plugins` 文件夹下创建一个 `.py` 文件即可。 
例如我们创建一个 `example.py` 。

```
pgp
├── data
├── pagermaid
├── languages
├── pyromod
└── plugins
    └── example.py
```

!> 请注意，插件名称不能存在重复

## 了解主修饰器

主修饰器（listener）是处理基本消息的主要修饰器。

### 主修饰器的基本组成

#### 主修饰器的类型

首先你需要确定你所要创建的插件是用于处理传入消息还是传出消息。
当处理传入消息时，你需要传入参数 `incoming=True`，
当处理传出消息时，你需要传入参数 `outgoing=True`。

#### 主修饰器的匹配规则

当你需要处理命令时，你需要传入参数 `command="命令"`，
当你需要处理其他消息时，你需要传入参数 `pattern="正则表达式"`。

当 command 和 pattern 都不为空时，主修饰器将会优先使用 pattern 。

!> 请注意，当 command 和 pattern 都为空时，主修饰器将会使此函数处理所有消息

#### 其余用户的触发权限

为方便管理，我们仅提供了两种触发权限，当传入参数 `need_admin=True` 时，
仅拥有 `plugins_root.command` 的 sudo 用户才能触发此插件。
当传入参数 `need_admin=False` 时，拥有 `plugins.command` 的 sudo 用户可以触发此插件。

#### 优先级

优先级代表此函数的执行顺序

!> 优先级数字越小越先响应！

默认优先级为 50 ，如果你想要改变优先级，可以传入参数 `priority=数字` 。

#### 阻断

当有任意函数发出了阻止传递信号时，
该消息将不再会传递给下一优先级，直接结束处理。

默认所有情况都不会阻断消息传递，如果你想修改，可以传入参数 `block_process=True` 。

在默认情况下，可以使用 `message.stop_propagation()` 方法动态阻止消息传递。

### 主修饰器的举例

默认情况下，你只需要填写修饰器中的这些参数：

```python
from pagermaid.listener import listener

@listener(command="命令",
          description="命令描述",
          usage="命令帮助")
```

## 定义处理函数

在 PGP 中，我们使用了 `依赖注入` 来帮助你动态管理需要的变量。

在默认情况下，你只需要获取触发函数的消息变量 `message: Message` 即可

```python
from pagermaid.enums import Message
from pagermaid.listener import listener

@listener(command="命令",
          description="命令描述",
          usage="命令帮助")
async def example(message: Message):
    # 在这里处理消息
    pass
```

## 进行消息操作

在对消息处理时，你可能需要调用 `message.edit()` 方法来编辑消息。

### 了解消息属性

[Pyrogram 文档](https://docs.pyrogram.org/api/types/Message#pyrogram.types.Message)

### 编辑消息

```python
async def example(message: Message):
    await message.edit("新的消息内容")
```

### 更多消息操作

[Pyrogram 文档](https://docs.pyrogram.org/api/bound-methods/#message)

## 进行客户端操作

### 发送消息

```python
from pagermaid.enums import Client
from pagermaid.listener import listener

@listener(command="命令",
          description="命令描述",
          usage="命令帮助")
async def example(bot: Client):
    # 向 Telegram 账号发送 你好
    await bot.send_message(777000, "你好")
```

### 更多客户端操作

[Pyrogram 文档](https://docs.pyrogram.org/api/methods)

## 插件示例

[GitHub](https://github.com/TeamPGM/PagerMaid_Plugins_Pyro/)
