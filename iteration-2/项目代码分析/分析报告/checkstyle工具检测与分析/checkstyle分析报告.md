# checkstyle 报告

## checkstyle 报告

### commit 0

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



### commit 1

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

### commit 2



### commit 3



## 修改的警告例子

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



## 对比人工 Debug



## 分析新增的警告



## 统计漏报的缺陷

漏报的缺陷，漏报的原因

## 统计工具本身缺陷

工具本身缺陷的数量 + 原因
