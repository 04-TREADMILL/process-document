### SentiStrength-SE note

#### 背景

SentiStrength和NLTK在软件工程领域中情感分析的准确性较低，特别是在检测负面情感方面。这突显了针对特定领域的情感分析工具的重要性，因为通用的情感分析工具可能无法捕捉到领域特定的语言和术语，从而导致低准确性。

这些情感分析工具是使用来自非技术社交媒体（例如Twitter帖子、论坛帖子、电影评论）的数据进行开发和训练的。当它们在技术领域（如软件工程）中操作时，它们的准确性显著下降，这主要是由于经常使用的技术术语在领域特定的含义上有所不同。

论文称软工领域文本当下的唯一可用数据集为Gold Standard Dataset，因此测试基本都在此数据集上进行。

#### 对于SentiStrength可以改进的地方的分析

对于SentiStrength在Gold Standard Dataset上测试的不准确结果，论文总结了如下原因：

1. 词语的领域特定含义，如support在软工中可能并没有正面情绪
2. 词语不同语境下的不同含义，please有时只是请求
3. 对于X的错误理解，X在日常用语中为kiss的意思，软工领域中指版本
4. 复制内容中的情绪词汇，如：代码注释
5. 对于否定的处理，SentiStrength必须要否定词紧邻情绪词才能识别
6. 词汇表缺少词汇，如apology
7. 拼写错误
8. 把重复的数字理解成booster word，如10001
9. 错误地检测专有名词，如有个同事叫做Harsh
10. 疑问句中的情绪词
11. 难以识别讽刺
12. 对于微妙表达难以理解

#### SentiSE的改进

##### 词汇表

SentiSE增加了167个正面情绪词汇和310个负面情绪词汇，也删除了一些词汇。

##### 启发式算法

1. 添加上下文信息以减少歧义，有些在构建情感词典时被中性化的词语，根据其前面的人称代词或所有格代词（如"I"、"we"、"my"、"he"、"she"、"you"）来判断是否表达了情感。
2. 引入中性化词语，观察到当一个情感词前面有一些中性化词语（如"would"、"could"、"should"、"might"）时，这个情感词会被中性化。
3. 将预处理阶段整合到算法中，包括过滤数字、代码片段、网址和堆栈跟踪信息等，同时添加拼写检查和忽略以问候语开头或跟随字符“@”的词语，以及将所有字母转换为小写。
4. 通过调整参数，提高了处理否定词的能力，使得在算法中设置一个可以检测到零到五个介于否定词和情感词之间的单词的范围，以减少困难。

#### 改进的评估

词汇表的更新有统计学上的显著意义；启发式算法无统计学显著意义
