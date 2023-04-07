# 原有架构

架构图如下

![native-arch](https://senti-strength.oss-cn-nanjing.aliyuncs.com/native-arch.png)

具体的

```
.
├── DemoApplication.java
├── Main.java
├── sentistrength
│   ├── BoosterWordsList.java
│   ├── ClassificationOptions.java
│   ├── ClassificationResources.java
│   ├── ClassificationStatistics.java
│   ├── Corpus.java
│   ├── CorrectSpellingsList.java
│   ├── EmoticonsList.java
│   ├── EvaluativeTerms.java
│   ├── IdiomList.java
│   ├── IronyList.java
│   ├── Lemmatiser.java
│   ├── NegatingWordList.java
│   ├── Paragraph.java
│   ├── QuestionWords.java
│   ├── Sentence.java
│   ├── SentimentWords.java
│   ├── SentiStrength.java
│   ├── Term.java
│   ├── Test.java
│   ├── TextParsingOptions.java
│   └── UnusedTermsClassificationIndex.java
├── utilities
│   ├── FileOps.java
│   ├── HelpOld.java
│   ├── SentiStrengthOld.java
│   ├── SentiStrengthTestAppletOld.java
│   ├── Sort.java
│   ├── StringIndex.java
│   └── Trie.java
└── wkaclass
    ├── Arff.java
    ├── PredictClass.java
    ├── Utilities.java
    ├── WekaCrossValidateInfoGain.java
    ├── WekaCrossValidateNoSelection.java
    ├── WekaDirectTrainClassifyEvaluate.java
    └── WekaMachineLearning.java
```
其中

- Main.java 是项目的入口程序，用于启动整个项目应用。
- sentistrength 该文件夹包含 SentiStrength 情感分析工具的源代码，主要实现了各种情感分析算法、词典库等功能。
  - BoosterWordsList：实现增强词（Booster words）列表的管理功能，用于提升文本的情感极性。
  - ClassificationOptions：定义了模型训练和分类时的一些参数和选项。
  - ClassificationResources：提供了资源文件的访问和管理接口。
  - ClassificationStatistics：实现了情感分类器的统计指标计算和评估功能。
  - Corpus：封装了语料库的操作和访问接口。
  - CorrectSpellingsList：实现了纠正拼写错误的功能。
  - EmoticonsList：提供了表情符号列表的管理功能。
  - EvaluativeTerms：实现了评价性词汇列表的管理功能。
  - IdiomList：提供了习语列表的管理功能。
  - IronyList：实现了判断文本中是否包含反讽语的功能。
  - Lemmatiser：定义了基于词形归并的词形还原接口。
  - NegatingWordList：定义了否定词列表的管理功能，用于将其它词汇的情感极性转变为相反态度。
  - Paragraph：实现了段落的分割和处理接口。
  - QuestionWords：定义了问题词的列表，用于判断文本中是否包含疑问。
- utilities 该文件夹包含一些实用工具类的源代码，例如文件操作、字符串操作、排序等。
  - FileOps：实现了文件操作的各种功能，例如读写文件、创建目录等。
  - HelpOld：提供了旧版本的帮助文档和命令行参数解析功能。
  - SentiStrengthOld：实现了旧版本的情感分析算法和数据结构。
  - SentiStrengthTestAppletOld：提供了旧版本的 GUI 界面测试程序。
  - Sort：实现了排序算法，例如快速排序、归并排序等。
  - StringIndex：定义了字符串索引接口，可以通过前缀或后缀查找字符串。
  - Trie：实现了字典树数据结构，用于快速搜索字符串。
- wkaclass 该文件夹包含基于 Weka 的分类器模块的源代码，主要实现了一些数据预处理、模型训练和评估等功能，用于构建机器学习模型进行分类任务。
  - Arff：实现了 ARFF 文件格式的读写和解析接口。
  - PredictClass：定义了预测类别的方法和接口。
  - Utilities：提供了一些实用的工具函数，例如字符串处理、文件读写等。
  - WekaCrossValidateInfoGain：实现了基于信息增益的 k 折交叉验证算法。
  - WekaCrossValidateNoSelection：实现了不进行特征选择的 k 折交叉验证算法。
  - WekaDirectTrainClassifyEvaluate：实现了直接训练分类器并进行评估的功能。
  - WekaMachineLearning：定义了机器学习算法的接口和实现，包括决策树、朴素贝叶斯、支持向量机等。