# checkstyle报告

## checkstyle报告

### commit 1

对原始代码进行Check，并生成报告

**警告情况**

| class                          | 警告类型 | 警告优先级 | 警告数量 |
| ------------------------------ | -------- | ---------- | -------- |
| BoosterWordList                |          |            | 183      |
| ClassificationOptions          |          |            | 251      |
| ClassificationResources        |          |            | 105      |
| ClassificationStatistics       |          |            | 547      |
| Corpus                         |          |            | 2341     |
| CorrectSpellingsList           |          |            | 87       |
| EvaluativeTerms                |          |            | 113      |
| IdiomList                      |          |            | 153      |
| IronyList                      |          |            | 57       |
| Lemmatister                    |          |            | 125      |
| NegatingWordList               |          |            | 74       |
| Paragraph                      |          |            | 586      |
| QuestionWords                  |          |            | 56       |
| Sentence                       |          |            | 964      |
| SentimentWords                 |          |            | 448      |
| SentiStrength                  |          |            | 1235     |
| Term                           |          |            | 467      |
| Test                           |          |            | 33       |
| TextParsingOptions             |          |            | 11       |
| UnusedTermsClassificationIndex |          |            | 436      |



### commit 2

利用IDEA自有的格式化代码功能，根据Google规则，格式化代码，消除大部分的警告

**警告情况**

| class                          | 警告类型 | 警告优先级 | 警告数量 |
| ------------------------------ | -------- | ---------- | -------- |
| BoosterWordList                |          |            | 31       |
| ClassificationOptions          |          |            | 34       |
| ClassificationResources        |          |            | 34       |
| ClassificationStatistics       |          |            | 164      |
| Corpus                         |          |            | 350      |
| CorrectSpellingsList           |          |            | 14       |
| EvaluativeTerms                |          |            | 17       |
| IdiomList                      |          |            | 22       |
| IronyList                      |          |            | 6        |
| Lemmatister                    |          |            | 22       |
| NegatingWordList               |          |            | 8        |
| Paragraph                      |          |            | 82       |
| QuestionWords                  |          |            | 6        |
| Sentence                       |          |            | 122      |
| SentimentWords                 |          |            | 79       |
| SentiStrength                  |          |            | 136      |
| Term                           |          |            | 56       |
| Test                           |          |            | 3        |
| TextParsingOptions             |          |            | 2        |
| UnusedTermsClassificationIndex |          |            | 85       |

**警告变化情况**

| class                          | close | new  | open |
| ------------------------------ | ----- | ---- | ---- |
| BoosterWordList                | 152   | 0    | 31   |
| ClassificationOptions          | 217   | 0    | 34   |
| ClassificationResources        | 71    | 0    | 34   |
| ClassificationStatistics       | 383   | 0    | 164  |
| Corpus                         | 1991  | 0    | 350  |
| CorrectSpellingsList           | 67    | 0    | 14   |
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

## commit 3



## 修改的警告例子



- 原有警告：Switch 块未定义 default 。 (96:7) [MissingSwitchDefault]
- 修改：添加default判断
- 警告原因：switch没有default块
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







## 分析新增的警告



## 统计漏报的缺陷数量



## 统计工具本身缺陷



