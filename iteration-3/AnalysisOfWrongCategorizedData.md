# Analysis of wrong categorized data

## 分类错误原因分析

### 标注错误

#### 斜体表示讽刺

negative;OK, so what do you want me to do about that? Hint: how about *telling us* what your problem is?;neutral

#### 大写表示情绪

negative;I had a memory crash on UIGraphicsGetImageFromCurrentImageContext() ... if you're creating and releasing a lot of them, you should wrap them in a fresh AutoReleasePool for each iteration. Even allowing the NSRunLoop to tick WAS NOT ENOUGH for Apple/iOS to do housekeeping on garbage lying around from this. e.g.;neutral

#### 描述情况不代表情绪

neutral;Typically you would handle that as a POST (not a GET), and read the xml from the request-stream (or there are helpers to let you do this). Otherwise URL encoding and length restrictions are going to make this extremely painful.;negative

neutral;Are you expecting to speed up the video without affecting the sound, or did the timer solution just make the sound aggressively awful?;negative

neutral;That's right, I have no plans to replace the existing system, sidecar is an excellent analogy.;positive

#### 对否定的处理

positive;"There is a setting in your setup project that will ""uninstall"" previous versions by default, turn this flag OFF, then you will not have to worry!";neutral

### 数据集错误

neutral;yeah: hopeless!;negative

positive;This worked for me.;neutral

negative;While we're at it, there is no such thing as Unicode. Well, there is, but it does not concern itself with earthly matters like files. There are numerous encodings which bridge that gap, but you don't appear to be aware of that or the difference this makes. See also: [The Absolute Minimum Every Software Developer Absolutely, Positively Must Know About Unicode and Character Sets (No Excuses!)](http://www.joelonsoftware.com/articles/Unicode.html));neutral

negative;"I had the problem that white was the ""Overscroll"" color, not actually the fading edge. try this (assuming you want a fading edge, but not the horrid white glare when you hit the ends! (otherwise set requires fading edge to none)):";neutral

negative;I have recently found out that anything Swing(NetBeans, IDEA) is excruciatingly slow to paint the UI over Remote Desktop(RDP). Can you guys give me any suggestion for something that will work properly over RDP?;neutral

## 预处理算法改进方向

1. 特殊处理斜体、大写、重复

2. 处理软工领域特定词汇，如 support，error，crash，bug，fix，这些单词在软工领域的意思更加中立

3. 词性分析，已识别是在描述客观事实还是在表达情绪

## 预处理总结

首先，我们参考了一些论文中的处理，做了如下处理：

1. 将缩写替换成本来的单词，如`can't`变为`cannot`。
  
2. 去除 URL，这对判断情感并无作用，其中的一些杂乱字符还有可能干扰情感判断。
  
3. 表情符号处理，现在的网络交流中，表达的方式很多变，表情则往往有效地帮助明确一句话的情感。我们考虑直接将表情替换为`PositiveSentiment`或`NegativeSentiment`。
  
4. 否定处理，在有否定含义的句子中，使用自然语言工具包（nltk）给一些词前面加上`NOT_`。
  
5. 去除 stop words，包括代码中的关键字等。
  
6. 去除代码片段，数据集中无疑有很多直接拷贝代码的情况，这些代码并不表示任何情感，也包括 HTML 标签，MarkDown 标签等。我们使用正则匹配删去了这些字符串。
  
7. 词干提取。为了帮助模型更好地理解语义，我们将单词的词干、基本形式或根形式提取出来。

8. 将文本中的专有词和实体词用标签替代，并处理在软工领域有特别含义的单词，如：support, bug, error。

### 实验数据：（详细数据见./result/2.txt）

| 预处理方法 | 预测准确率 |
| --- | --- |
| 原有方法 | 82.50%/82.88% |
| 原有方法 + 替换专有词和实体词 | 81.90% |
| 原有方法 + 处理领域特定单词 | 82.65% |
| 原有方法 + 处理斜体 | 82.43% |
| 原有方法 + 处理大写 | 82.58% |
| 原有方法 + 处理斜体、大写 | 82.80%/82.58% |
| 原有方法 + 处理斜体、大写 + 处理领域特定单词 | 82.65%/82.58% |

- 实验结论：在 TF-IDF 和 GradientBoostingClassifier 的条件下，与处理算法对于结果的影响不大。