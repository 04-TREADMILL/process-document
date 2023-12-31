# iteration three

在迭代三中，本小组选择了方向二——算法优化，主要尝试了机器学习式、大模型和提示工程等方法，并尝试结合了词典、预处理、数据扩增、数据集扩充等辅助手段，最终最优预测结果准确度为 0.9079939668174962，使用了 openai fine-tune 的方法。

所有的代码和数据在仓库 https://github.com/04-TREADMILL/se-text-sa 中，本目录下总结了算法优化的相关文档与结果。

下面是对本目录结构的说明：

- 预处理：预处理模块的文档与结果
- 停止词：停止词模块的文档与结果
- 爬虫：指向一个爬虫子仓库，其中介绍了扩充数据集构造的方法
- 论文阅读：包含了两个相关论文 SentiStrength-SE 和 SESSION 的阅读笔记
- 其他文件：主要分析分类错误的原因
- **optimization.md**：核心**优化说明文档**，对应的结果保存在 results 文件夹中
- 最终结果：展示了三种算法优化方法下的运行结果与对应的模型和日志，包括
    - openai fine-tune 准确度为 0.9079939668174962
    - tfidf embedding 配合 sklearn classifier 准确度为 0.8642533936651584
    - openai embedding 配合 sklearn classifier 准确度为 0.8378582202111614