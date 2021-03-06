# NLP Chinese Data Augmentation 一键中文数据增强工具

使用：`pip install nlpcda`

---

## 介绍

一键中文数据增强工具，支持：
- 随机实体替换
- 近义词
- 近义近音字替换
- 随机字删除

在不改变原文的情况下生成指定数量的训练语料文本

Email:425776024@qq.com

---
## API

### 随机【（等价）实体】替换

参数：
- base_file ：缺省时使用内置（公司）实体。对公司实体进行替换
    > 是文本文件路径，内容形如：\
    > 实体1\
    > 实体2\
    > ...\
    > 实体n
- create_num=3 ：返回最多3个增强文本
- change_rate=0.3 ： 文本改变率
- seed ： 随机种子

```python
from nlpcda.tools.randomword import Randomword

test_str = '''这个天大药业很不错啊，测试测试。这是一场疫情防控的人民战争、总体战、阻击战，习近平总书记亲自指挥、亲自部署。运筹帷幄 指挥若定始终把人民群众生命安全和身体健康放在第一位'''
smw = Randomword(create_num=3, change_rate=0.3)
rs1 = smw.replace(test_str)

print('随机实体替换>>>>>>')
for s in rs1:
    print(s)
'''
随机实体替换>>>>>>
这个天大药业很不错啊，测试测试。这是一场疫情防控的人民战争、总体战、阻击战，习近平总书记亲自指挥、亲自部署。运筹帷幄 指挥若定始终把人民群众生命安全和身体健康放在第一位
这个中国通信服务很不错啊，测试测试。这是一场疫情防控的人民战争、总体战、阻击战，习近平总书记亲自指挥、亲自部署。运筹帷幄 指挥若定始终把人民群众生命安全和身体健康放在第一位
这个瑞丰光电很不错啊，测试测试。这是一场疫情防控的人民战争、总体战、阻击战，习近平总书记亲自指挥、亲自部署。运筹帷幄 指挥若定始终把人民群众生命安全和身体健康放在第一位
'''

```

### 随机同义词替换
参数：
- base_file ：缺省时使用内置同义词表，你可以设定/自己指定更加丰富的同义词表：
    > 是文本文件路径，内容形如（空格隔开）：\
    > Aa01A0 人类 生人 全人类\
    > id2 同义词b1 同义词b2 ... 同义词bk\
    > ...\
    > idn 同义词n1 同义词n2\
- create_num=3 ：返回最多3个增强文本
- change_rate=0.3 ： 文本改变率
- seed ： 随机种子

```python
from nlpcda.tools.similarword import Similarword

test_str = '''这个天大药业很不错啊，测试测试。这是一场疫情防控的人民战争、总体战、阻击战，习近平总书记亲自指挥、亲自部署。运筹帷幄 指挥若定始终把人民群众生命安全和身体健康放在第一位'''
smw = Similarword(create_num=3, change_rate=0.3)
rs1 = smw.replace(test_str)

print('随机同义词替换>>>>>>')
for s in rs1:
    print(s)

'''
随机同义词替换>>>>>>
这个天大药业很不错啊，测试测试。这是一场疫情防控的人民战争、总体战、阻击战，习近平总书记亲自指挥、亲自部署。运筹帷幄 指挥若定始终把人民群众生命安全和身体健康放在第一位
这天大药业很毋庸置疑啊，测试测试。这是一场疫情失控的鸦片战争、总体战、阻击战，习近平总书记亲指挥、亲自布置。筹措 指挥若定辄把人民群众生命安全和身体健康放在第一位
这个天大药业很不错啊，测试测试。这是一场疫情防控的人民战争、总体战、阻击战，习近平总书记亲自指挥、亲自布。运筹帷幄 指挥若定尽把人民群众生命安全和身体健康放在第一位
'''

```

### 随机近义字替换
参数：
- base_file ：缺省时使用内置【同义同音字表】，你可以设定/自己指定更加丰富的同义同音字表：
    > 是文本文件路径，内容形如（空格隔开）：\
    > de	的	地	得	德	嘚	徳	锝	脦	悳	淂	鍀	惪	恴	棏\
    > 拼音2 字b1 字b2 ... 字bk\
    > ...\
    > 拼音n 字n1 字n2\
- create_num=3 ：返回最多3个增强文本
- change_rate=0.3 ： 文本改变率
- seed ： 随机种子
```python
from nlpcda.tools.homophone import Homophone

test_str = '''这个天大药业很不错啊，测试测试。这是一场疫情防控的人民战争、总体战、阻击战，习近平总书记亲自指挥、亲自部署。运筹帷幄 指挥若定始终把人民群众生命安全和身体健康放在第一位'''
smw = Homophone(create_num=3, change_rate=0.3)
rs1 = smw.replace(test_str)

print('随机近义字替换>>>>>>')
for s in rs1:
    print(s)

'''
随机近义字替换>>>>>>
这个天大药业很不错啊，测试测试。这是一场疫情防控的人民战争、总体战、阻击战，习近平总书记亲自指挥、亲自部署。运筹帷幄 指挥若定始终把人民群众生命安全和身体健康放在第一位
籷个兲大药业很部错啊，测试测視。这駛义场幆情防控的人民战争、总体战、阻击战，习埐平总輸记亲自指挥、亲胔部署。运筹帷仴 指挥若定始终把靱民群众生命安全和身体健钪放在第一蝛
这个天大药业很不错啊，测试萴试。这蒔一鱨疫情防悾的人民榐争、总蹄战、阻击詹，吸近平昮鄃羈吢嗞指挥、懃自瓿署。运筹骩幄 憄挥若椗匙终把人民群众生命安牷和身体監康放在第一位
'''

```

### 随机字删除
参数：
- create_num=3 ：返回最多3个增强文本
- change_rate=0.3 ： 文本改变率
- seed ： 随机种子
```python
from nlpcda.tools.randomdeletechar import RandomDeleteChar

test_str = '''这个天大药业很不错啊，测试测试。这是一场疫情防控的人民战争、总体战、阻击战，习近平总书记亲自指挥、亲自部署。运筹帷幄 指挥若定始终把人民群众生命安全和身体健康放在第一位'''
smw = RandomDeleteChar(create_num=3, change_rate=0.3)
rs1 = smw.replace(test_str)

print('随机字删除>>>>>>')
for s in rs1:
    print(s)

'''
随机字删除>>>>>>
这个天大药业很不错啊，测试测试。这是一场疫情防控的人民战争、总体战、阻击战，习近平总书记亲自指挥、亲自部署。运筹帷幄 指挥若定始终把人民群众生命安全和身体健康放在第一位
这个天大药业不错啊，测试测试这是一场疫情防控人民战争总体战、阻击战，习近平总书记亲自指挥亲自部署运筹帷幄 指挥若定始终人民群众生命安全和身体健康放在
这个天大药业不错，测试测试这是一场疫情防控的人民战争、总体战阻击战习近平总书记亲自指挥、亲自部署。运筹帷幄指挥若定始终人民群众生命安全身体健康放在
'''

```

### 添加自定义词典
用于使用之前，增加分词效果
```python
from nlpcda.tools.randomword import Randomword
from nlpcda.tools.similarword import Similarword
from nlpcda.tools.homophone import Homophone
from nlpcda.tools.randomdeletechar import RandomDeleteChar

Randomword.add_word('张杰')
Randomword.add_words(['张杰','谢娜','马化腾','中国人民银行'])
# Similarword，Homophone，RandomDeleteChar 同上

```