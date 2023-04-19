# checkstyle 报告

## checkstyle 报告

### commit 1

对原始代码进行 Check，并生成报告

**警告情况**

| class                          | 警告类型 | 警告数量 |
| ------------------------------ | -------- | -------- |
| BoosterWordList                | error    | 183      |
| ClassificationOptions          | error    | 251      |
| ClassificationResources        | error    | 105      |
| ClassificationStatistics       | error    | 547      |
| Corpus                         | error    | 2341     |
| CorrectSpellingsList           | error    | 87       |
| EvaluativeTerms                | error    | 113      |
| IdiomList                      | error    | 153      |
| IronyList                      | error    | 57       |
| Lemmatister                    | error    | 125      |
| NegatingWordList               | error    | 74       |
| Paragraph                      | error    | 586      |
| QuestionWords                  | error    | 56       |
| Sentence                       | error    | 964      |
| SentimentWords                 | error    | 448      |
| SentiStrength                  | error    | 1235     |
| Term                           | error    | 467      |
| Test                           | error    | 33       |
| TextParsingOptions             | error    | 11       |
| UnusedTermsClassificationIndex | error    | 436      |



### commit 2

利用 IDEA 自有的格式化代码功能，根据 Google 规则，格式化代码，消除大部分的警告

**警告情况**

| class                          | 警告类型 | 警告数量 |
| ------------------------------ | -------- | -------- |
| BoosterWordList                | error    | 31       |
| ClassificationOptions          | error    | 34       |
| ClassificationResources        | error    | 34       |
| ClassificationStatistics       | error    | 164      |
| Corpus                         | error    | 350      |
| CorrectSpellingsList           | error    | 14       |
| EvaluativeTerms                | error    | 17       |
| IdiomList                      | error    | 22       |
| IronyList                      | error    | 6        |
| Lemmatister                    | error    | 22       |
| NegatingWordList               | error    | 8        |
| Paragraph                      | error    | 82       |
| QuestionWords                  | error    | 6        |
| Sentence                       | error    | 122      |
| SentimentWords                 | error    | 79       |
| SentiStrength                  | error    | 136      |
| Term                           | error    | 56       |
| Test                           | error    | 3        |
| TextParsingOptions             | error    | 2        |
| UnusedTermsClassificationIndex | error    | 85       |

**警告变化情况**

| class                          | close | new  | open |
| ------------------------------ | ----- | ---- | ---- |
| BoosterWordList                | 152   | 0    | 31   |
| ClassificationOptions          | 217   | 0    | 23   |
| ClassificationResources        | 71    | 0    | 29   |
| ClassificationStatistics       | 383   | 0    | 164  |
| Corpus                         | 1991  | 0    | 350  |
| CorrectSpellingsList           | 67    | 0    | 16   |
| EvaluativeTerms                | 96    | 0    | 17   |
| IdiomList                      | 131   | 0    | 22   |
| IronyList                      | 51    | 0    | 6    |
| Lemmatister                    | 103   | 0    | 22   |
| NegatingWordList               | 66    | 0    | 8    |
| Paragraph                      | 504   | 0    | 82   |
| QuestionWords                  | 50    | 0    | 6    |
| Sentence                       | 842   | 0    | 122  |
| SentimentWords                 | 369   | 0    | 79   |
| SentiStrength                  | 1099  | 0    | 136  |
| Term                           | 411   | 0    | 56   |
| Test                           | 30    | 0    | 3    |
| TextParsingOptions             | 9     | 0    | 2    |
| UnusedTermsClassificationIndex | 351   | 0    | 85   |

### commit 3

整体重构后的警告情况

| class                          | 警告类型 | 警告数量 |
| ------------------------------ | -------- | -------- |
| BoosterWordList                | error    | 43       |
| ClassificationOptions          | error    | 104      |
| ClassificationResources        | error    | 65       |
| ClassificationStatistics       | error    | 186      |
| BaseCorpus                     | error    | 501      |
| BinaryModeCorpus               | error    | 84       |
| ScaleModeCorpus                | error    | 85       |
| TrinayModeCorpus               | error    | 85       |
| CorrectSpellingsList           | error    | 23       |
| EvaluativeTerms                | error    | 39       |
| IdiomList                      | error    | 43       |
| IronyList                      | error    | 14       |
| Lemmatister                    | error    | 35       |
| NegatingWordList               | error    | 17       |
| Paragraph                      | error    | 119      |
| QuestionWords                  | error    | 15       |
| Sentence                       | error    | 202      |
| SentimentWords                 | error    | 102      |
| SentiStrength                  | error    | 239      |
| Term                           | error    | 92       |
| Test                           | error    | 14       |
| TextParsingOptions             | error    | 9        |
| UnusedTermsClassificationIndex | error    | 117      |
| WordPresenceList               | error    | 3        |
| EmoticonsList                  | error    | 18       |

**警告变化情况**

| class                          | close | new  | open |
| ------------------------------ | ----- | ---- | ---- |
| BoosterWordList                | 0     | 12   | 43   |
| ClassificationOptions          | 0     | 80   | 104  |
| ClassificationResources        | 0     | 31   | 65   |
| ClassificationStatistics       | 0     | 24   | 186  |
| Corpus                         | 350   | 0    | 0    |
| BaseCorpus                     | 0     | 501  | 501  |
| BinaryModeCorpus               | 0     | 84   | 84   |
| ScaleModeCorpus                | 0     | 85   | 85   |
| TrinaryModeCorpus              | 0     | 85   | 85   |
| CorrectSpellingsList           | 0     | 9    | 23   |
| EvaluativeTerms                | 0     | 22   | 39   |
| IdiomList                      | 0     | 19   | 43   |
| IronyList                      | 0     | 8    | 14   |
| Lemmatister                    | 0     | 13   | 35   |
| NegatingWordList               | 0     | 9    | 17   |
| Paragraph                      | 5     | 37   | 119  |
| QuestionWords                  | 0     | 9    | 15   |
| Sentence                       | 14    | 80   | 202  |
| SentimentWords                 | 0     | 23   | 102  |
| SentiStrength                  | 24    | 103  | 239  |
| Term                           | 1     | 36   | 92   |
| Test                           | 0     | 11   | 14   |
| TextParsingOptions             | 0     | 7    | 9    |
| UnusedTermsClassificationIndex | 0     | 34   | 119  |
| WordPresenceList               | 0     | 0    | 3    |
| EmotionsList                   | 0     | 0    | 18   |

## 修改的警告例子

### case1

**Term.java**

- 原有警告：Switch 块未定义 default。 (96:7) [MissingSwitchDefault]
- 修改：添加 default 判断
- 警告原因：switch 没有 default 块
- 修改原因：对非法的字段进行过滤，检查无效字段

```Java
//Term.java
      switch (iLastCharType) {
        case 1:
          this.codeWord(sWordAndPunctuation);
          break;
        case 2:
          this.codePunctuation(sWordAndPunctuation);
        default:
          System.err.println(iLastCharType + " is invalid!!!");
          break;
      }
```

### case2

**BoosterWordList.java line="68" column="33"**

- 原有警告："Parameter name &apos;iExtraBlankArrayEntriesToInclude&apos; must match pattern \&apos;\^\[a-z](\[a-z0-9][a-zA-Z0-9]*)?$&apos;."
- 修改：删除该参数
- 警告原因：iExtraBlankArrayEntriesToInclude 命名不符合规范
- 修改原因：Booster Word List 还提供了添加 Booster Word 的方法，但由于这个方法在代码中没有使用过，为了方便基类的继承，就删除了这个方法参数

### case3

***Sentence.java line="51" column="3"***

- 原有警告："CTOR_DEF”之前应该有一个空白行"
- 修改：将该空白行删除
- 警告原因：不符合 Google_style 规则
- 修改原因：格式化代码规范

### case4

***Sentence.java line="1034" column="92"***

- 原有警告："&apos;+&apos; 应另起一行。"
- 修改：将 '+' 另起一行
- 警告原因：不符合 Google_style 规则
- 修改原因：便于观察条件判断

### case5

**SentiStrength.java line="1080" column="7"**

- 原有警告："变量&apos;iTrinary&apos;声明及第一次使用距离 4 行（最多：3 行）。若需要存储该变量的值，请将其声明为 final 的（方法调用前声明以避免副作用影响原值）"
- 修改：将声明语句统一移动到代码块首部
- 警告原因：iTrinary 变量声明及第一次使用距离 4 行
- 修改原因：统一将声明移动到代码块首部，提高可读性

### case 6

**ClassificationStatistics.java line="475" column="3"**

- 原有警告："所有重载的方法都应该相邻放置。在相同类型的重载方法之间放置非重载方法是违反的。最后一个重载方法在行 &apos;317&apos; 上"
- 修改：移动重载方法的位置
- 警告原因：重载方法的位置放置错误
- 修改原因：将相同类型的重载方法相邻放置，提高可维护性

### case 7

**ClassificationOptions.java line="39" column="18"**

- 警告信息："变量 &apos;bgTensiStrength&apos; 应定义为 private 的，并为其创建访问方法"
- 修改：通过 getter 方法获取成员变量
- 警告原因：成员变量 public
- 原因：防止对外暴露过多资源

## 新增的警告

### 重构导致新增

`SentiStrength.java`

- 警告信息：<error line="1067" column="3" severity="warning" message="Return 次数 4 次（最大允许非空虚方法/ 拉姆达：3 次）。" source="com.puppycrawl.tools.checkstyle.checks.coding.ReturnCountCheck"/>
- 警告原因：一个方法内部 return 语句过多
- 不修改
- 此处我们对 SentiStrength 进行了重构，在对应的条件分支进行 return 操作，反而有利于代码的维护

### 新增检查规则

`BaseCorpus.java`

- 警告信息：<error line="182" column="24" severity="warning" message="&apos;2&apos; 是一个魔术数字（直接常数）。" source="com.puppycrawl.tools.checkstyle.checks.coding.MagicNumberCheck"/>
- 警告原因：新增的 alibaba 规则判定为常数
- 不修改
- 原因：虽然该变量多次使用，值均不变，但是为了代码的可读性更高，我们对于这类检测为常量的变量仍做保留的处理

`ClassificationOptions.java`

- 警告信息：<error line="39" column="18" severity="warning" message="变量 &apos;bgTensiStrength&apos; 应定义为 private 的，并为其创建访问方法。" source="com.puppycrawl.tools.checkstyle.checks.design.VisibilityModifierCheck"/>
- 警告原因：成员变量 public
- 修改：通过 getter 方法获取成员变量
- 原因：防止对外暴露过多资源

`ClassificationStatistics.java`

- 警告信息：<error line="475" column="3" severity="warning" message="所有重载的方法都应该相邻放置。在相同类型的重载方法之间放置非重载方法是违反的。最后一个重载方法在行 &apos;317&apos; 上。" source="com.puppycrawl.tools.checkstyle.checks.coding.OverloadMethodsDeclarationOrderCheck"/>
- 警告原因：相同类型的重载方法之间防止其他内容
- 修改：改变重载方法之间的位置
- 原因：提高可读性



## 基于 SonarLint 的部分报告对照

### 去除冗余的类型转换

不必要的类型转换会使代码更加晦涩难懂，如`Paragraph.java`类中的表达式：`this.igPositiveSentiment = (int) Math.round(((double) (fTotalPos + (float) iPosWords) + 0.45D) / (double) iPosWords);`

根据 java 语法，这里将 int 和 float 转化为 double 的操作是不必要的。我们将上面的式子重构为：`this.igPositiveSentiment = (int) Math.round(((fTotalPos + iPosWords) + 0.45D) / iPosWords);`

重构对象：对 ClassificationStatistics.java、Corpus.java、Paragraph.java、Sentence.java、SentiStrength.java、SentimentWords.java、Arff.java、Predict.java。

结果不一一列举

### 方法和类遵循驼峰命名规则

检查了方法名规范，只有一种例外，如`i_Sort()`标识某个方法是供 int 型使用，我们遵循原先的命名方式。

重构对象：ClassificationStatistics.java、Corpus.java、Paragraph.java、WekaCrossValidateInfoGain.java、WekaCrossValidateNoSelection.java，此外重构了软件包的名字，"WekaClass"、"SentiStrength"

### 去除冗余的数组参数创建

对于不知道有几个参数的情况即 varargs(...) 参数，创建数组并没有什么价值，反而会使开发者迷惑应该以数组为单独对象还是当作集合。例如：

```java
//原代码
method.invoke(urlClassLoader, new Object[] {u});
//修改后
method.invoke(urlClassLoader, u);
```

重构对象：

Utilities.java, WekaCrossValidateInfoGain.java, WekaCrossValidateNoSelection.java, WekaDirectTrainClassifyEvaluate.java

### 在 for 循环条件判断和自增语句上直接进行循环要做的操作

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

### 建议使用 java.nio.files#delete

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

### 字符串比较应该用 equals()

观察到在比较字符串时，有使用"=="进行比较，考虑将它进行修改。

重构对象：EvaluativeTerms.java

### 可能的以 0 为分母的计算

在做除法前，对变量应该进行检查。

重构对象：ClassificationStatistics.java、Arff.java

### switch 应该有 default 分支

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

### 返回空数组而不是 null

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

## 对比人工 Debug

//Todo 缺陷 + 原因

## 统计工具本身缺陷

为了进行对照，我们同时使用了 Sonarlint 检测工具对代码进行报告（对应报告位于 Sonarlint 文件夹下）

认为 checkstyle 工具本身具有如下的缺陷

### 局限性

Checkstyle 的主要目标是检查代码的风格和结构问题，而不是语义问题。例如，Checkstyle 无法检测代码中的逻辑错误、运行时错误、并发问题、安全问题等。因此，开发者仍然需要进行其他类型的测试，例如单元测试、集成测试、性能测试等。

相比之下，Sonarlint 可以检测一些简单逻辑错误，和部分的语义问题，对于开发效率的提升更大

### 检测结果的可读性差

Checkstyle 的检测结果通常是一份 XML 报告，需要借助其他工具或插件才能更好地展示和分析。

相比之下，Soarlint 可以以 Pdf 和 Html 可视化的形式展现代码的 bug，对于错误率和归因也有较好的总结

### 误报

Checkstyle 可能会出现误报或漏报，导致开发者需要手动调整或检查代码。

例如，Checkstyle 将各类初始化声明和使用的距离作为报错点，个人在某些情况下这种编写规范是允许的

### 漏报

从上述材料可以看出，checkstyle 无论是相比人工，还是其他工具，会存在不同程度的漏报，这会导致开发者仍需要对代码进行仔细地 debug

### 仅支持 Java 语言

对于其他语言不能够很好的检测

### 无法检测代码质量

checkstyle 只能检测代码地格式和结构，但是对于代码的质量很难给出有效的建议，因此需要人工重构才能提高代码的可读性，维护性以及可用性。

