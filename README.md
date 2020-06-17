## 搜狗细胞词库（.scel）转换工具

### 简介

该项目参考 [scel2txt](https://github.com/lewang0/scel2txt ) ，在此表示感谢

### 用法

#### 直接输出至文本

```shell
scel.py [file] [dest]
```

输出的 dest 格式为 "词语\t拼音\t优先级"

参数详解:

- file	搜狗细胞词库文件，格式为 .scel 如果不指定则会自动从官网获取“网络流行新词【官方推荐】.scel”
- dest	输出的文件，如果不指定则会输出到标准输出

#### 当成库使用

从文件读取

```python
import scel
s = scel.scel()
s.load('网络流行新词【官方推荐】.scel')
print(s.title)
print(s.category)
print(s.description)
print(s.samples)
print("一共有 %d 个词汇" % len(s.word_list))
print("第一个词是 %s" % str(s.word_list[0]))
print("一共有 %d 个被删除的词汇" % len(s.del_words))
```

从官网获取流行词汇

```python
import scel
s = scel.scel()
data = scel.getInternetPopularNewWords()
s.loads(data)
print(s.title)
print(s.category)
print(s.description)
print(s.samples)
print("一共有 %d 个词汇" % len(s.word_list))
print("第一个词是 %s" % str(s.word_list[0]))
print("一共有 %d 个被删除的词汇" % len(s.del_words))
```

