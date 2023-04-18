# SentiStrength 运行结果分析报告

### 运行情况

针对软工文本的 sof4423 数据集、appreview 数据集，社交文本的 myspace1041 数据集、bbc1000 数据集，我们运行了 sentistrength 代码，对每条文本项给出三分类预测结果：1(积极)、0(中性)、-1(消极) ，并将其与原数据集中的人工标注结果进行比对。

### 数据处理

以人工标注结果为标准答案作为参照，分别计算了混淆矩阵、准确率、精度、召回率和 F1 分数，并画出了对应的 ROC 曲线和精确率 - 召回率曲线。具体结果如下：

```json
/*------------------------- myspace -------------------------*/
confusion_mat: {
	pos_real: {'pos_pred': 606, 'neg_pred': 65, 'neu_pred': 31},
	neg_real: {'pos_pred': 42, 'neg_pred': 70, 'neu_pred': 20},
	neu_real: {'pos_pred': 98, 'neg_pred': 49, 'neu_pred': 60}}
accuracy:	0.63053
precision:	{'pos': 0.81233, 'neg': 0.38043, 'neu': 0.54054}
recall:		{'pos': 0.86325, 'neg': 0.5303, 'neu': 0.28986}
f1_score:	{'pos': 0.83702, 'neg': 0.44303, 'neu': 0.37736}

/*--------------------------- bbc ---------------------------*/
confusion_mat: {
	pos_real: {'pos_pred': 59, 'neg_pred': 23, 'neu_pred': 17},
	neg_real: {'pos_pred': 78, 'neg_pred': 524, 'neu_pred': 51},
	neu_real: {'pos_pred': 44, 'neg_pred': 135, 'neu_pred': 69}}
accuracy:	0.58962
precision:	{'pos': 0.32597, 'neg': 0.76833, 'neu': 0.50365}
recall:		{'pos': 0.59596, 'neg': 0.80245, 'neu': 0.27823}
f1_score:	{'pos': 0.42143, 'neg': 0.78502, 'neu': 0.35845}

/*--------------------------- sof ---------------------------*/
confusion_mat: {
	pos_real: {'pos_pred': 1410, 'neg_pred': 88, 'neu_pred': 29},
	neg_real: {'pos_pred': 27, 'neg_pred': 1120, 'neu_pred': 55},
	neu_real: {'pos_pred': 149, 'neg_pred': 468, 'neu_pred': 1077}}
accuracy:	0.73047
precision:	{'pos': 0.88903, 'neg': 0.66826, 'neu': 0.92765}
recall:		{'pos': 0.92338, 'neg': 0.93178, 'neu': 0.63577}
f1_score:	{'pos': 0.90588, 'neg': 0.77832, 'neu': 0.75446}

/*----------------------- appreview ------------------------*/
confusion_mat: {
	pos_real: {'pos_pred': 163, 'neg_pred': 17, 'neu_pred': 6},
	neg_real: {'pos_pred': 50, 'neg_pred': 66, 'neu_pred': 14},
	neu_real: {'pos_pred': 14, 'neg_pred': 10, 'neu_pred': 1}}
accuracy:	0.60568
precision:	{'pos': 0.71806, 'neg': 0.70968, 'neu': 0.04762}
recall:		{'pos': 0.87634, 'neg': 0.50769, 'neu': 0.04}
f1_score:	{'pos': 0.78934, 'neg': 0.59193, 'neu': 0.04348}
```

其中，*pos* 表示 1(积极情绪)，*neg* 表示 -1(消极情绪)，*neu* 表示 0(中性情绪)

<img src="https://pictures-1312865652.cos.ap-nanjing.myqcloud.com/image-20230330212141984.webp" alt="image-20230330212141984" style="zoom:50%;" />

其中，左侧对应数据集 myspace1041，右侧对应数据集 bbc1000

<img src="https://pictures-1312865652.cos.ap-nanjing.myqcloud.com/image-20230330211957990.webp" alt="image-20230330211957990" style="zoom:50%;" />

其中，左侧对应数据集 sof4423，右侧对应数据集 appreview

### 结果分析

由数据分析结果可以看出，sentistrength 在软工文本数据集 sof4423 上的预测效果相对较好，在社交文本数据集 myspace1041、bbc1000 上和软工文本数据集 appreview 上效果其次。sentistrength 在给定的数据集上的预测表现与文本类型为软工文本或社交文本没有显示出必然的联系。

- 在 bbc1000 数据集上，sentistrength 对消极情绪的预测更为准确。
- 在 myspace1041 数据集上，sentistrength 对积极情绪的预测更为准确。
- 在 sof4423 数据集上，sentistrength 对积极、消极和中性情绪的预测都有相对较好的表现。
- 在 appreview 数据集上，sentistrength 对积极情绪的预测更为准确，对中性情绪的预测完全不准确。

针对软工文本，我们将 sentistrength 预测错误的文本项提取出来进行了人工分析，得到如下可能的出错原因：

- 模型本身的缺陷

    - 没有正确理解否定词（no worries 被预测成消极）

    - 中性问句中包含被设定成消极的词汇，情绪被预测成消极
    - 没有正确理解转折，错误预测了情感倾向
    - 错误理解含有消极词汇但没有消极语义的固定句式（I‘m afraid）
    - 在陈述中使用一些消极词汇但没有消极情绪

- 文本自身的缺陷

    - 偶然拼写错误导致模型错误理解语义

- 软工文本的特殊之处
    - 软工文本中，开头表达同意倾向于表达积极情绪，即使主体内容缺少情绪色彩（I agree，+1）
    - 软工文本中，一些和软件系统状态相关的词汇往往能传达情绪（work，not work，link is down）
    - 软工文本中，对软件系统 bug 的描述倾向于含有消极情绪
    - 软工文本中，讨论技术时包含的样例代码片段不应当成为情绪预测的依据
    - 软工文本中，有许多单用程度副词或短语表示消极情绪的场景

### 概括总结

大多数情况下：

- 对于积极的情绪表达，社交文本更加直接和强烈（大写字母、标点符号），软工文本更加理性和克制
- 对于消极的情绪表达，社交文本的表达形式更多样（辱骂、讽刺、抱怨等），软工文本更具软工特色（bug 难以处理等）

社交文本中更多地使用表情符号和缩写，也存在更多或故意或无意的拼写错误，情感表达更为随意、非正式和符号化，理论上来说会对基于词汇表的模型在情绪预测中造成更多的干扰，需要针对不规范的文字表达进行特殊的处理。

软工文本中更多地使用专业术语和具体的功能描述，语言使用相对工整规范，情感表达更为理性和客观，但软工术语可能会包含特定语境下特殊的情感倾向，需要针对其情感表达的特点进行特殊的处理。

无论是社交文本抑或是软工文本，当文本长度较长时，使用基于词汇表的算法可能难以准确把握文本中的情感倾向，出现“以偏概全”的现象，即以对个别单词的打分影响对整个文本情绪的判断。



