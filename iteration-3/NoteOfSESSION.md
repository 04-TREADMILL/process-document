# SESSION

## 背景及概述

现有的改进词典（Senti-SE），学习式的效果不好。

SESSION方法分为三步。首先，我们预处理输入的SE文本，并使用Stanford CoreNLP进行分割。其次，我们使用过滤规则来确定一个句子是否能够触发后续的分析。第三，我们使用调整规则来增强SentiStrength的原始输出。值得注意的是，我们的方法对SentiStrength的词典没有任何更改。

## Filter Rules 从句过滤规则

符合以下任意一种模式都可以触发情感分析。

### 1) Direct Sentiment Pattern

给定的一句话符合直接情感模式的六种情况如下：

1. 包含感叹号；
2. 包含在SentiStrength的表情符号列表中记录的表情符号，例如“**:)**”；
3. 包含感叹词，如“哇”等；
4. 包含四个以“fu”、“da”、“sh”和“he”开头的脏话中的任意一个；
5. 至少一个从句以情感词开头（除了“please”和“plz”）；
6. 是一条祈使句，且情感密度大于0.3。

### 2) Decorated Sentiment Pattern

Decorated Sentiment Pattern是指在句子中包含形容词或副词的情感词，或情感词被形容词或副词修饰。此外，还有一些常用的副词，如“always”、“even”和“still”，可以被用来修饰情感词。

### 3) "About Me" Pattern

当一句话符合以下四种情况之一时，即可被归类为“关于我”模式：

1. 句子的主语是“I”，并且包含了一个情感词（例如“I like…”）；
2. 句子包含一个情感动词，后面跟着“me”这个宾语（例如“…confuse me”）；
3. 句子包含一个情感形容词或名词，后面跟着“me”（例如“…make me confused”）；
4. 句子中包含一个被“my”修饰的情感词（例如“This was my bad.”）

### 4) "Judgment" Pattern

1. "be动词 + 情感形容词/名词"（例如："It’s ugly and inefficient"）；
2. "代词 + 情感动词"（例如："This sucks so much."）；
3. "get + 情感词"（例如："The problem just gets worse."）；
4. "情感名词 + be动词"（例如："The biggest reason for failure is your carelessness"）；
5. "a/an/the + 形容词 + 名词"（例如："It has an excellent command line interface."）。

## Adjust Rules 改进的算法

### 1) Recognizing Subjunctive Mood

虚拟语气表达了作者的主观愿望、怀疑、建议或假设，但不表达真实的情感。因此，在虚拟语气子句中出现的情感词将被忽略。我们的方法通过识别“if”和“unless”作为给定句子子句中的条件副词来识别虚拟语气。我们不会在这些子句中识别情感。例如，在句子“If you're really worried about this, Java is not the language for you.”中，消极的情感词“worried”在虚拟语气子句中，因此它不反映任何事实，也不表达作者的情感。

### 2) Identifying Polysemous Words by the Sentence Structure

SentiStrength为每个情感词分配情感得分。然而，当情感词根据不同的句子结构表达不同的含义时，单个情感得分可能会导致错误的结果。在我们的观察中，我们总结了几个容易导致错误的多义词。这些词被分类为两组。我们基于词性标签确认第一组词的含义，基于它们与其他词的搭配确认第二组词的含义。

### 3) Dealing with Negations

SentiStrength中关于否定的原始规则是，当否定词紧跟在情感词前时，将情感词的极性乘以−0.5来翻转极性。这个规则过于强烈，忽略了太多的否定场景，特别是对于SE文本。例如，这个文本“not to worry, it was a permissions issue with the file.”根据原始的否定规则，其情感将被识别为积极，但我们将其标记为中性。相反，在我们的方法中，否定词列表中的单词和以“’t”结尾的单词（例如“isn’t”）将使其后三个单词（“to”除外）内的词的情感变为中性。我们还添加了另外三个单词“nothing”、“no”和“without”（不在SentiStrength的原始否定列表中），以使其后面的第一个单词（“to”除外）的情感变为中性。添加的这三个否定词的限定否定范围是因为它们的词性是名词或介词，而原始列表中的否定词或以“’t”结尾的词是助动词。

## 总结

Filter Rules和Adjust Rules都有用，但用处都不太大。Filter Rules对于中性情感多的数据集更有用。

### 总的

![sun.t5-p11-sun-large.gif (820×319) (ieee.org)](https://ieeexplore.ieee.org/mediastore_new/IEEE/content/media/9462945/9462957/9462971/sun.t5-p11-sun-large.gif)

### Filter Rules和Adjust Rules分别

![sun.t8-p11-sun-large.gif (820×322) (ieee.org)](https://ieeexplore.ieee.org/mediastore_new/IEEE/content/media/9462945/9462957/9462971/sun.t8-p11-sun-large.gif)