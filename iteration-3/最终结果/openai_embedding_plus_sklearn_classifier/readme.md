model:

- 该模型的 Embedding 操作借助 OpenAI 的 Embedding 服务获取，选择了 text-embedding-ada-002 模型（可由任何有效的 OpenAI API_KEY 访问）
- 该模型的分类器由 sklearn 库中的 SGDClassifier 完成，训练好的分类器已保存为 SGD-text-embedding-ada-002-2023-05-21-19-54-23.pkl（见当前目录）
- 调用方法：先通过 OpenAI API_KEY 调用 text-embedding-ada-002 模型将文本转换为向量，再将向量作为训练好的 SGDClassifier 的输入得到预测结果

train:

- 代码示意如下（详见 analyzer.py 中的 OpenAIEmbedderAnalyzer 类的 train 方法）：
    classifier = SGDClassifier()
    text_emb_train = get_embeddings(text_train)
    classifier.fit(text_emb_train, label_train)
    save_model(classifier)
- 由于训练由 sklearn 库直接完成，没有留下训练日志

test:

- 测试结果详见当前目录下 result.txt