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

# 重构设计

## 1. SentiStrength.java

### 1.1 复杂嵌套 if-else 的重构

1. SentiStrength 类中，`initialiseAndRun`等方法频繁出现类似如下的语句，if-else 层层嵌套，跨越几百行，而且往下翻会发现其实只会执行 if 对应的几行语句，就直接退出函数了。

```java
if(){
    if(){}else{}
} else if(){

} else if(){

}
return;
```

这样的代码风格，需要花费很多时间才能读懂执行了哪些语句，不利于后续开发维护，因此考虑重构。改为如下的语句：

```java
if(){return;}
if(){return;}
if(){
    if() return;
}
...
```

这样可以清晰的知道符合某一条件时应该执行哪些语句，也明确了何时会退出方法，不需要跨越大几百行阅读嵌套 if-else。

### 1.2 复用代码段的提取

对于结果的分析，`SentiStrength.java`中多次出现一段计算结果评分的代码，如`parseOneText, listenForCmdInput, listenAtPort`方法中，都有使用，因此我们将`int iPos; int iNeg; int iTrinary; int iScale; String outputMessage;`封装为了`OutputVO`类，将重复代码封装为`computeSentimentScores`方法，计算情感评分并返回`OutputVO`。

```java
public OutputVO computeSentimentScores(String sentence, String separator) {
        OutputVO output = new OutputVO();
        Paragraph paragraph = new Paragraph();
        paragraph.setParagraph(sentence, this.c.resources, this.c.options);
        output.setINeg(paragraph.getParagraphNegativeSentiment());
        output.setIPos(paragraph.getParagraphPositiveSentiment());
        output.setITrinary(paragraph.getParagraphTrinarySentiment());
        output.setIScale(paragraph.getParagraphScaleSentiment());
        String sRationale = "";
        if (this.c.options.bgEchoText) {
            sRationale = separator + sentence;
        }

        if (this.c.options.bgExplainClassification) {
            sRationale = separator + paragraph.getClassificationRationale();
        }

        if (this.c.options.bgTrinaryMode) {
            output.setOutputMessage(output.getIPos() + separator + output.getINeg() + separator + output.getITrinary() + sRationale);
        } else {
            output.setOutputMessage(this.c.options.bgScaleMode ? output.getIPos() + separator + output.getINeg() + separator + output.getIScale() + sRationale :
                    output.getIPos() + separator + output.getINeg() + sRationale);
        }
        return output;
    }
```

### 1.3 其他

将 for 语句改为强化的 for 语句：``for (File listOfFile : listOfFiles)``

删除了无效的代码，例如几次出现的`while(true){while(true){}}`嵌套死循环

## 2. Corpus 的重构

corpus 中有许多方法，动辄数百行，看起来极为繁琐复杂。观察到其实很多方法的复杂其实是来自于 SentiStrength 对情感的分析有几种模式：三元模式、三元模式二元版、比例模式，和普通模式（POS，NEG）。因此我们将原先的 Corpus 重命名为`BaseCorpus`，对应普通模式，并创建了三个子类：`TrinaryModeCorpus`，`BinaryModeCorpus`，`ScaleCorpus`。继承`BaseCorpus`，并重写了一些方法。

### 2.1 indexClassifiedCorpus 方法

原先的`indexClassifiedCorpus`

```java
public void indexClassifiedCorpus()
{
    unusedTermsClassificationIndex = new UnusedTermsClassificationIndex();
    if(options.bgScaleMode)
    {
        unusedTermsClassificationIndex.initialise(true, false, false, false);
        for(int i = 1; i <= igParagraphCount; i++)
            paragraph[i].addParagraphToIndexWithScaleValues(unusedTermsClassificationIndex, igScaleCorrect[i], igScaleClass[i]);

    } else
    if(options.bgTrinaryMode && options.bgBinaryVersionOfTrinaryMode)
    {
        unusedTermsClassificationIndex.initialise(false, false, true, false);
        for(int i = 1; i <= igParagraphCount; i++)
            paragraph[i].addParagraphToIndexWithBinaryValues(unusedTermsClassificationIndex, igTrinaryCorrect[i], igTrinaryClass[i]);

    } else
    if(options.bgTrinaryMode && !options.bgBinaryVersionOfTrinaryMode)
    {
        unusedTermsClassificationIndex.initialise(false, false, false, true);
        for(int i = 1; i <= igParagraphCount; i++)
            paragraph[i].addParagraphToIndexWithTrinaryValues(unusedTermsClassificationIndex, igTrinaryCorrect[i], igTrinaryClass[i]);

    } else
    {
        unusedTermsClassificationIndex.initialise(false, true, false, false);
        for(int i = 1; i <= igParagraphCount; i++)
            paragraph[i].addParagraphToIndexWithPosNegValues(unusedTermsClassificationIndex, igPosCorrect[i], igPosClass[i], igNegCorrect[i], igNegClass[i]);

    }
}
```

不难看到，看似很长的方法，其实就是由不同模式的 if 语句组成，修改后可以使代码清晰许多，这里以`ScaleModeCorpus`为例，重写为：

```java
@Override
public void indexClassifiedCorpus() {
    unusedTermsClassificationIndex.initialise(true, false, false, false);
    for (int i = 1; i <= igParagraphCount; i++) {
        paragraph[i].addParagraphToIndexWithScaleValues(unusedTermsClassificationIndex,
                igScaleCorrect[i], igScaleClass[i]);
    }
}
```

### 2.2 printCorpusUnusedTermsClassificationIndex 方法

和上面类似的重构，不足是有少量重复代码

```java
//原 Corpus 代码
public void printCorpusUnusedTermsClassificationIndex(String saveFile, int iMinFreq)
{
    if(!bgCorpusClassified)
        calculateCorpusSentimentScores();
    if(unusedTermsClassificationIndex == null)
        indexClassifiedCorpus();
    if(options.bgScaleMode)
        unusedTermsClassificationIndex.printIndexWithScaleValues(saveFile, iMinFreq);
    else
    if(options.bgTrinaryMode && options.bgBinaryVersionOfTrinaryMode)
        unusedTermsClassificationIndex.printIndexWithBinaryValues(saveFile, iMinFreq);
    else
    if(options.bgTrinaryMode && !options.bgBinaryVersionOfTrinaryMode)
        unusedTermsClassificationIndex.printIndexWithTrinaryValues(saveFile, iMinFreq);
    else
        unusedTermsClassificationIndex.printIndexWithPosNegValues(saveFile, iMinFreq);
    System.out.println("Term weights saved to " + saveFile);
}
//TrinaryModeCorpus
@Override
public void printCorpusUnusedTermsClassificationIndex(String saveFile, int iMinFreq) {
    if (!bgCorpusClassified) {
        calculateCorpusSentimentScores();
    }
    if (unusedTermsClassificationIndex == null) {
        indexClassifiedCorpus();
    }
    unusedTermsClassificationIndex.printIndexWithScaleValues(saveFile, iMinFreq);
    System.out.println("Term weights saved to " + saveFile);
}
```

### 2.3 setCorpus 方法

这个方法如果简单的拆出 if 语句，会显得过于冗余，因为前后都有大量重复的代码，因此考虑在 BaseCorpus 中拆出根据模式处理数据的代码，作为新的方法`processorForSetCorpus`，子类只需要重写这一部分即可。

```java
//原代码示意
public boolean setCorpus(String sInFilenameAndPath)
{
    if(resources == null && !resources.initialise(options))
        return false;
    igParagraphCount = FileOps.i_CountLinesInTextFile(sInFilenameAndPath) + 1;
    if(igParagraphCount <= 2)
    {
        igParagraphCount = 0;
        return false;
    }
    paragraph = new Paragraph[igParagraphCount];
    igPosCorrect = new int[igParagraphCount];
    igNegCorrect = new int[igParagraphCount];
    igTrinaryCorrect = new int[igParagraphCount];
    igScaleCorrect = new int[igParagraphCount];
    bgSupcorpusMember = new boolean[igParagraphCount];
    igParagraphCount = 0;
    try
    {
        BufferedReader rReader = new BufferedReader(new FileReader(sInFilenameAndPath));
        String sLine;
        if(rReader.ready())
            sLine = rReader.readLine();
        while((sLine = rReader.readLine()) != null) {
            if(!sLine.equals(""))
            {
                ...//处理数据的代码
            }
        }
    }
}
```

提取上面的`...`部分并重写，以`BinaryModeCorpus`为例：

```java
@Override
protected void processorForSetCorpus(String sLine) {
    paragraph[++igParagraphCount] = new Paragraph();
    int iLastTabPos = sLine.lastIndexOf("\t");
    int iFirstTabPos = sLine.indexOf("\t");
    if (iFirstTabPos < iLastTabPos ||
            iFirstTabPos > 0) {
        paragraph[igParagraphCount].setParagraph(sLine.substring(iLastTabPos + 1), resources,
                options);
        try {
            igTrinaryCorrect[igParagraphCount] =
                    Integer.parseInt(sLine.substring(0, iFirstTabPos).trim());
        } catch (Exception e) {
            System.out.println(
                    "Trinary classification could not be read and will be ignored!: " + sLine);
            igTrinaryCorrect[igParagraphCount] = 999;
        }
        if (igTrinaryCorrect[igParagraphCount] > 1 ||
                igTrinaryCorrect[igParagraphCount] < -1) {
            System.out.println(
                    "Trinary classification out of bounds and will be ignored!: " + sLine);
            igParagraphCount--;
        } else if (igTrinaryCorrect[igParagraphCount] == 0) {
            System.out.println("Warning, unexpected 0 in binary classification!: " + sLine);
        }
    } else {
        if (iFirstTabPos >= 0) {
            igTrinaryCorrect[igParagraphCount] =
                    Integer.parseInt(sLine.substring(0, iFirstTabPos).trim());
            sLine = sLine.substring(iFirstTabPos + 1);
        } else {
            igTrinaryCorrect[igParagraphCount] = 0;
        }
        paragraph[igParagraphCount].setParagraph(sLine, resources, options);
        igPosCorrect[igParagraphCount] = 0;
        igNegCorrect[igParagraphCount] = 0;
    }
}
```

### 2.4 其他重构的方法枚举

重构基本就是以上思路，不再赘叙，涉及重构的方法还有：`calculateCorpusSentimentScores`、`reClassifyClassifiedCorpusForSentimentChange`、`processorForClassifyAllLinesAndRecordWithID`、`processorForAnnotateAllLinesInInputFile`、`printClassificationResultsRow`。

### 2.5 子类的使用

我们的重构设计符合**里氏替换原则**，因此只需要在合适的位置将 Corpus 换为子类即可。在`SentiStrength.java`中，在`parseParametersForCorpusOptions`方法中解析命令确定运行模式，因此我们在那一步将 corpus 换为对应的模式，例如：

```java
if (args[i].equalsIgnoreCase("binary")) {
    this.c.options.bgBinaryVersionOfTrinaryMode = true;
    this.c.options.bgTrinaryMode = true;
    bArgumentRecognised[i] = true;
    this.c = new BinaryModeCorpus(c.options, c.resources);
}
```

## 3. 根据一些原则进行的重构

### 3.1 去除冗余的类型转换

不必要的类型转换会使代码更加晦涩难懂，如`Paragraph.java`类中的表达式：`this.igPositiveSentiment = (int) Math.round(((double) (fTotalPos + (float) iPosWords) + 0.45D) / (double) iPosWords);`

根据 java 语法，这里将 int 和 float 转化为 double 的操作是不必要的。我们将上面的式子重构为：`this.igPositiveSentiment = (int) Math.round(((fTotalPos + iPosWords) + 0.45D) / iPosWords);`

重构对象：对 ClassificationStatistics.java、Corpus.java、Paragraph.java、Sentence.java、SentiStrength.java、SentimentWords.java、Arff.java、Predict.java。

结果不一一列举，我们人工检查到的都是对 int、float、double 类型的冗余转换，并未找到其他。

### 3.2 方法和类遵循驼峰命名规则

检查了方法名规范，只有一种例外，如`i_Sort()`标识某个方法是供 int 型使用，我们遵循原先的命名方式。

重构对象：ClassificationStatistics.java、Corpus.java、Paragraph.java、WekaCrossValidateInfoGain.java、WekaCrossValidateNoSelection.java，此外重构了软件包的名字，"WekaClass"、"SentiStrength"

### 3.3 去除冗余的数组参数创建

对于不知道有几个参数的情况即 varargs(...) 参数，创建数组并没有什么价值，反而会使开发者迷惑应该以数组为单独对象还是当作集合。例如：

```java
//原代码
method.invoke(urlClassLoader, new Object[] {u});
//修改后
method.invoke(urlClassLoader, u);
```

重构对象：

Utilities.java, WekaCrossValidateInfoGain.java, WekaCrossValidateNoSelection.java, WekaDirectTrainClassifyEvaluate.java

### 3.4 在 for 循环条件判断和自增语句上直接进行循环要做的操作

在检查中，有多次看到例如这样的代码：

`for (i = 0; i < 99 && Objects.requireNonNull(sLabelledArffFiles)[i] != null && !sLabelledArffFiles[i].equals(""); ++i) {}`

`for (iCol = 1; iCol <= iAttributeCount; iIndex[iCol] = iCol++) {}`

直接在条件判断和自增中就把要干的活干了，看似精简，但也很难懂，因此对它进行了修改：

`for (i = 0; i < 99; ++i) {
 if (Objects.requireNonNull(sLabelledArffFiles)[i] == null) break;
 if (sLabelledArffFiles[i].equals("")) break;
}`

`for (iCol = 1; iCol <= iAttributeCount; iCol++) {
 iIndex[iCol] = iCol;
}`

重构对象：arff.java

### 3.5 建议使用 java.nio.files#delete

项目中有许多对文件的操作，删除也是其中之一，项目中使用 java.io.File#delete，这个方法在失败时并不会提示错误原因，因此我们将它优化为 java.nio.files#delete

示例如下：

```java
//原代码
File original = new File(sInputFile);
original.delete();
//修改后
Path original= Paths.get(sInputFile);
Files.delete(original);
```

重构对象：Corpus.java、FileOps.java、Arff.java

### 3.6 字符串比较应该用 equals()

观察到在比较字符串时，有使用"=="进行比较，考虑将它进行修改。

重构对象：EvaluativeTerms.java

### 3.7 可能的以 0 为分母的计算

在做除法前，对变量应该进行检查。

重构对象：ClassificationStatistics.java、Arff.java

### 3.8 switch 应该有 default 分支

```java
      switch (iLastCharType) {
        case 1:
          this.codeWord(sWordAndPunctuation);
          break;
        case 2:
          this.codePunctuation(sWordAndPunctuation);
      //补上
        default:
          System.err.println(iLastCharType + " is invalid!!!");
          break;
      }
```

重构对象：Term.java

### 3.9 返回空数组而不是 null

对于方法的返回值，当它为数组时，即使长度为 0，我们也应该返回空数组，而不是 null，以避免错误的产生。

```java
//原代码
public String[] getInput() {
        return null;
}
//修改后
public String[] getInput() {
        return new String[0];
}
```

重构对象：SentiStrength.java、Arff.java

### 3.10 其他

合并了一些 if 条件，去除了冗余的变量赋值，使用 standardCharSets