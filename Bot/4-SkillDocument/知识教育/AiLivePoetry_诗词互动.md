
# 1. 服务简介

当前的诗词Bot产品主要为一问一答的播报功能，但缺少与用户更为丰富和沉浸的互动，诗词问答会以闯关形式通过与用户的更多交互满足需求

# 2.槽位

| **Slot\_Key** | **Description** | **Example** |
| --- | --- | --- |
| title | 诗词名 | 静夜思 |
| author | 诗词作者 | 李白 |
| verse | 单句诗词 | 床前明月光 |

# 3.意图

## 3.1 Learn_学

 我要**学**静夜思
 
## 3.2 Read_跟读

我要**跟读**静夜思

## 3.3 Abut_对答

我要**对答**静夜思

## 3.4 Recite_背

我要**背诵**静夜思

## 3.5 Next_下一关

下一关

## 3.6 Prev_上一关

上一关

## 3.7 Repeat_重复

重复学习

## 3.8 Exit_退出

退出

# 4.返回结果

返回结果如下json所示。
语音输出方案在response的result字段里的outputSpeech中，以数组的形式，依次读出。目前支持PlainText格式和ssml格式。

返回results中data字段说明：

| **Field** | **Description** | **Example** | **type** |
| --- | --- | --- | --- |
| title | 诗词名 | 静夜思 | string |
| author | 诗词作者 | 李白 | []string |
| content | 当前显示内容 | 床前明月光 | []string |
| dynasty | 朝代 | 唐代 | []string |
| index | content字段最后末尾诗句下标 | -1 | int |
| length | 诗句总字数 | 20 | int |
| lines | 诗句总句数 | 4 | int |
| state | 用户回复正确与否标记 | right | string |


## 4.1 Learn_学

query: 我要学静夜思

response:

```
  "results": [
    {
      "hint": "跟我一起学吧，静夜思，唐朝，李白，床前明月光，疑是地上霜，举头望明月，低头思故乡，知识要多次记忆才能掌握，是重复学习？还是进入下一关？",
      "outputSpeech": {
        "items": [
          {
            "type": "SSML",
            "source": "<p>跟我一起学吧</p>\n<p>静夜思</p>\n<p><s>唐朝</s><s>李白</s></p>"
          },
          {
            "type": "SSML",
            "source": "<s>床前<break time=\"100ms\" /><emphasis>明</emphasis>月光</s>\n<s>疑是<break time=\"100ms\" /><emphasis>地</emphasis>上霜</s>\n<s>举头<break time=\"100ms\" /><emphasis>望</emphasis>明月</s>\n<s>低头<break time=\"100ms\" /><emphasis>思</emphasis>故乡</s>"
          },
          {
            "type": "PlainText",
            "source": "知识要多次记忆才能掌握，是重复学习？还是进入下一关？"
          }
        ]
      },
      "emotions": [
        {
          "type": "answer",
          "level": 11,
          "code": "L001"
        }
      ],
      "data": {
        "author": [
          "李白"
        ],
        "content": [
          "床前明月光",
          "疑是地上霜",
          "举头望明月",
          "低头思故乡"
        ],
        "dynasty": [
          "唐朝"
        ],
        "index": 3,
        "length": 20,
        "lines": 4,
        "state": "",
        "title": "静夜思"
      }
    }
  ]
```

## 4.2 Read_跟读

query：我要跟读静夜思

response：

```
   "results": [
    {
      "hint": "跟我读，静夜思，唐朝，李白，床前明月光，该你拉",
      "outputSpeech": {
        "items": [
          {
            "type": "SSML",
            "source": "<p>跟我读</p>\n<p>静夜思</p>\n<p><s>唐朝</s><s>李白</s></p>"
          },
          {
            "type": "SSML",
            "source": "<s>床前<break time=\"100ms\" /><emphasis>明</emphasis>月光</s>"
          },
          {
            "type": "PlainText",
            "source": "该你拉"
          }
        ]
      },
      "emotions": [
        {
          "type": "answer",
          "level": 0,
          "code": "A001"
        }
      ],
      "data": {
        "author": [
          "李白"
        ],
        "content": [
          "床前明月光"
        ],
        "dynasty": [
          "唐朝"
        ],
        "index": 0,
        "length": 20,
        "lines": 4,
        "state": "",
        "title": "静夜思"
      }
    }
  ]
```

## 4.3 Abut_对答

queyr：我要对静夜思

response：

```
  "results": [
    {
      "hint": "跟我对，静夜思，唐朝，李白，床前明月光，该你拉",
      "outputSpeech": {
        "items": [
          {
            "type": "SSML",
            "source": "<p>跟我对</p>\n<p>静夜思</p>\n<p><s>唐朝</s><s>李白</s></p>"
          },
          {
            "type": "SSML",
            "source": "<s>床前<break time=\"100ms\" /><emphasis>明</emphasis>月光</s>"
          },
          {
            "type": "PlainText",
            "source": "该你拉"
          }
        ]
      },
      "emotions": [
        {
          "type": "answer",
          "level": 10,
          "code": "K001"
        }
      ],
      "data": {
        "author": [
          "李白"
        ],
        "content": [
          "床前明月光"
        ],
        "dynasty": [
          "唐朝"
        ],
        "index": 0,
        "length": 20,
        "lines": 4,
        "state": "",
        "title": "静夜思"
      }
    }
  ]
```

## 4.4 Recite_背

query：我要背静夜思

response：

```
  "results": [
    {
      "hint": "你来背，静夜思，唐朝，李白，，该你拉",
      "outputSpeech": {
        "items": [
          {
            "type": "SSML",
            "source": "<p>你来背</p>\n<p>静夜思</p>\n<p><s>唐朝</s><s>李白</s></p>"
          },
          {
            "type": "PlainText",
            "source": "该你拉"
          }
        ]
      },
      "emotions": [
        {
          "type": "answer",
          "level": 0,
          "code": "A001"
        }
      ],
      "data": {
        "author": [
          "李白"
        ],
        "content": null,
        "dynasty": [
          "唐朝"
        ],
        "index": -1,
        "length": 20,
        "lines": 4,
        "state": "",
        "title": "静夜思"
      }
    }
  ]
```

## 4.5 Next_下一关

query：下一关 （假定当前关是**对答**）

response：

```
  "results": [
    {
      "hint": "你来背，静夜思，唐朝，李白，，轮到你拉",
      "outputSpeech": {
        "items": [
          {
            "type": "SSML",
            "source": "<p>你来背</p>\n<p>静夜思</p>\n<p><s>唐朝</s><s>李白</s></p>"
          },
          {
            "type": "PlainText",
            "source": "轮到你拉"
          }
        ]
      },
      "emotions": [
        {
          "type": "answer",
          "level": 0,
          "code": "A001"
        }
      ],
      "data": {
        "author": [
          "李白"
        ],
        "content": null,
        "dynasty": [
          "唐朝"
        ],
        "index": -1,
        "length": 20,
        "lines": 4,
        "state": "",
        "title": "静夜思"
      }
    }
  ]
```

## 4.6 Prev_上一关

query:上一关（假定当前关是**对答**）

response：

```
  "results": [
    {
      "hint": "跟我读，静夜思，唐朝，李白，床前明月光，轮到你拉",
      "outputSpeech": {
        "items": [
          {
            "type": "SSML",
            "source": "<p>跟我读</p>\n<p>静夜思</p>\n<p><s>唐朝</s><s>李白</s></p>"
          },
          {
            "type": "SSML",
            "source": "<s>床前<break time=\"100ms\" /><emphasis>明</emphasis>月光</s>"
          },
          {
            "type": "PlainText",
            "source": "轮到你拉"
          }
        ]
      },
      "emotions": [
        {
          "type": "answer",
          "level": 0,
          "code": "A001"
        }
      ],
      "data": {
        "author": [
          "李白"
        ],
        "content": [
          "床前明月光"
        ],
        "dynasty": [
          "唐朝"
        ],
        "index": 0,
        "length": 20,
        "lines": 4,
        "state": "",
        "title": "静夜思"
      }
    }
  ]
```

## 4.7 Repeat_重复

query：重复学习（只有在**整首诗完成**后才能进入）

response：

```
 "results": [
    {
      "hint": "跟我读，静夜思，唐朝，李白，床前明月光，轮到你拉",
      "outputSpeech": {
        "items": [
          {
            "type": "SSML",
            "source": "<p>跟我读</p>\n<p>静夜思</p>\n<p><s>唐朝</s><s>李白</s></p>"
          },
          {
            "type": "SSML",
            "source": "<s>床前<break time=\"100ms\" /><emphasis>明</emphasis>月光</s>"
          },
          {
            "type": "PlainText",
            "source": "轮到你拉"
          }
        ]
      },
      "emotions": [
        {
          "type": "answer",
          "level": 0,
          "code": "A001"
        }
      ],
      "data": {
        "author": [
          "李白"
        ],
        "content": [
          "床前明月光"
        ],
        "dynasty": [
          "唐朝"
        ],
        "index": 0,
        "length": 20,
        "lines": 4,
        "state": "",
        "title": "静夜思"
      }
    }
  ]
```

## 4.8 Exit_退出

query：退出

response：

```
 "results": [
    {
      "hint": "好的",
      "outputSpeech": {
        "items": [
          {
            "type": "PlainText",
            "source": "好的"
          }
        ]
      },
      "emotions": [
        {
          "type": "answer",
          "level": 0,
          "code": "A001"
        }
      ]
    }
  ]
```

# 5.超时事件

request：

```
{
    "event": {
        "name": "ROSAI.TimeoutEvent",
        "type": "dedicated",
        "data" : {
          "service": "AiLivePoetry"
        }
    },
    "params": {
      "repeat": 1
    },
    "clientId": "4000006F00000001",
    "agentId": "Dc3OTE2YTczNDJhO",
    "token": "c6e30bd939f18f224173a843beda940c"
}
```

response：

```
{
    "reqId": "Dc3OTE2YTczNDJhO-4000006F00000001-1532421578294537341",
    "status": {
        "code": 0
    },
    "results": [
        {
            "hint": "小朋友，我找不到你了，我们下次再来玩吧",
            "outputSpeech": {
                "items": [
                    {
                        "type": "PlainText",
                        "source": "小朋友，我找不到你了，我们下次再来玩吧"
                    }
                ]
            }
        }
    ]
}
```


