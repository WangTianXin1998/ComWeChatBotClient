# 消息段
本项目目前实现了部分标准消息段及拓展消息段
:::tip onebot12
表示聊天消息的一个部分，在一些平台上，聊天消息支持图文混排，其中就会有多个消息段，分别表示每个图片和每段文字。
:::

## `text` 纯文本<Badge text="标准" type="success" />
表示一段纯文本。
 - [x] 可以接收
 - [x] 可以发送

::: tabs
@tab 参数
| 字段名    | 数据类型 | 说明       |
| :-------: | :------: | :--------: |
| `text`    | string   | 纯文本内容 |

@tab 示例
```json
{
    "type": "text",
    "data": {
        "text": "这是一个纯文本"
    }
}
```

@tab nb2使用
``` python
from nonebot.adapters.onebot.v12 import MessageSegment

message = MessageSegment.text("这是一个纯文本")
```
:::
## `mention` 提及（即 @）<Badge text="标准" type="success" />

表示at某人。

::: warning 注意场景

此消息段只有在群聊时才可使用

:::

- [x] 可以接收
- [x] 可以发送

::: tabs

@tab 参数

|  字段名   | 数据类型 |     说明     |
| :-------: | :------: | :----------: |
| `user_id` |  string  | 提及用户的id |

@tab 示例

```json
{
    "type": "mention",
    "data": {
        "user_id": "1234567"
    }
}
```

@tab nb2使用
```python
from nonebot.adapters.onebot.v12 import MessageSegment

message = MessageSegment.mention(user_id="123456")
```

:::

## `mention_all` 提及所有人<Badge text="标准" type="success" />

表示at所有人。

::: danger 注意权限

没有at所有人权限，请不要尝试发送此消息段

:::

- [x] 可以接收
- [x] 可以发送

::: tabs

@tab 参数

无。

@tab 示例

```json
{
    "type": "mention_all",
    "data": {}
}
```

@tab nb2使用
```python
from nonebot.adapters.onebot.v12 import MessageSegment

message = MessageSegment.mention_all()
```

:::

## `image` 图片<Badge text="标准" type="success" />

表示一张图片。

- [x] 可以接收
- [x] 可以发送

::: tabs

@tab 参数

|  字段名   | 数据类型 |    说明     |
| :-------: | :------: | :---------: |
| `file_id` |  string  | 图片文件 ID |

@tab 示例

```json
{
    "type": "image",
    "data": {
        "file_id": "e30f9684-3d54-4f65-b2da-db291a477f16"
    }
}
```

@tab nb2使用
```python
from nonebot.adapters.onebot.v12 import MessageSegment

message = MessageSegment.image(file_id="e30f9684-3d54-4f65-b2da-db291a477f16")
```

:::

## `voice` 语音<Badge text="标准" type="success" />

表示一段语音消息。

- [x] 可以接收
- [ ] 可以发送

::: tabs

@tab 参数

|  字段名   | 数据类型 |    说明     |
| :-------: | :------: | :---------: |
| `file_id` |  string  | 语音文件 ID |

@tab 示例

```json
{
    "type": "voice",
    "data": {
        "file_id": "e30f9684-3d54-4f65-b2da-db291a477f16"
    }
}
```



:::

## `audio` 音频<Badge text="标准" type="success" />

音频文件。

::: warning 未实现

本应用未实现此字段

:::

## `video` 视频<Badge text="标准" type="success" />

视频消息

- [x] 可以接收
- [ ] 可以发送

:::tabs

@tab 参数

|  字段名   | 数据类型 |    说明     |
| :-------: | :------: | :---------: |
| `file_id` |  string  | 视频文件 ID |

@tab 示例

```json
{
    "type": "video",
    "data": {
        "file_id": "e30f9684-3d54-4f65-b2da-db291a477f16"
    }
}
```



:::

## `file` 文件<Badge text="标准" type="success" />

文件消息

- [x] 可以接收
- [x] 可以发送

:::tabs

@tab 参数

|  字段名   | 数据类型 |    说明     |
| :-------: | :------: | :---------: |
| `file_id` |  string  |     文件 ID |

@tab 示例

```json
{
    "type": "file",
    "data": {
        "file_id": "e30f9684-3d54-4f65-b2da-db291a477f16"
    }
}
```

@tab nb2使用
```python
from nonebot.adapters.onebot.v12 import MessageSegment

message = MessageSegment.file(file_id="e30f9684-3d54-4f65-b2da-db291a477f16")
```

:::

## `location` 位置<Badge text="标准" type="success" />

位置消息。

- [x] 可以接收
- [ ] 可以发送

::: tabs

@tab 参数

|   字段名    | 数据类型 |   说明   |
| :---------: | :------: | :------: |
| `latitude`  | float64  |   纬度   |
| `longitude` | float64  |   经度   |
|   `title`   |  string  |   标题   |
|  `content`  |  string  | 地址内容 |

@tab 示例

```json
{
    "type": "location",
    "data": {
        "latitude": 31.032315,
        "longitude": 121.447127,
        "title": "上海交通大学闵行校区",
        "content": "中国上海市闵行区东川路800号"
    }
}
```

:::



## `reply` 回复<Badge text="标准" type="success" />

回复消息。

:::info wechat

在微信里，为引用消息

:::

- [x] 可以接收
- [ ] 可以发送

::: tabs

@tab 参数

|    字段名    | 数据类型 |        说明         |
| :----------: | :------: | :-----------------: |
| `message_id` |  string  |    回复的消息 ID    |
|  `user_id`   |  string  | 回复的消息发送者 ID |

@tab 示例

```json
{
    "type": "reply",
    "data": {
        "message_id": "6283",
        "user_id": "1234567"
    }
}
```



:::

## `wx.emoji` 表情<Badge text="拓展" type="danger" />
表示表情消息

::: warning 与图片区别
在微信里，图片消息指直接发送图片；而表情为动态gif表情包等
:::
 - [x] 可以接收
 - [x] 可以发送
::: tabs

@tab 参数

|  字段名   | 数据类型 |    说明     |
| :-------: | :------: | :---------: |
| `file_id` |  string  | 图片文件 ID |

@tab 示例

```json
{
    "type": "wx.emoji",
    "data": {
        "file_id": "e30f9684-3d54-4f65-b2da-db291a477f16"
    }
}
```

@tab nb2使用
```python
from nonebot.adapters.onebot.v12 import MessageSegment

message = MessageSegment("wx.emoji",{"file_id":"e30f9684-3d54-4f65-b2da-db291a477f16"})
```

:::

## `wx.link` 链接<Badge text="拓展" type="danger" />
文章链接消息
 - [x] 可以接收
 - [x] 可以发送
## `wx.app` 小程序<Badge text="拓展" type="danger" />