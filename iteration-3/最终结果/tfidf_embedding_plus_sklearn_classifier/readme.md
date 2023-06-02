model:

- 该模型的 Embedding 操作使用 sklearn 库的 TfidfVectorizer 在训练集上完成，训练好的向量化模型已保存为 embedding-2023-05-21-19-41-39.pkl（见当前目录）
- 该模型的分类器由 sklearn 库中的 SGDClassifier 完成，训练好的分类器已保存为 RF-local-2023-05-21-19-41-39.pkl（见当前目录）
- 调用方法：先通过训练好的 TfidfVectorizer 模型将文本转换为向量，再将向量作为训练好的 RandomForestClassifier 的输入得到预测结果

train:

- 代码示意如下（详见 analyzer.py 中的 TFIDFAnalyzer 类的 train 方法）：
    classifier = RandomForestClassifier()
    vectorizer = TfidfVectorizer(tokenizer=self.preprocessor.tokenize_and_stem, sublinear_tf=True, max_df=0.5, stop_words=self.preprocessor.stop_words, min_df=3)
    text_emb_train = vectorizer.fit_transform(text_train)
    classifier.fit(text_emb_train, label_train)
    save_model(vectorizer)
    save_model(classifier)
- 其中，self.preprocessor.tokenize_and_stem 和 self.preprocessor.stop_words 分别为借助 nltk 库实现的 tokenizer 和自构建的停用词表，详见 preProcessor.py
- 由于训练由 sklearn 库直接完成，没有留下训练日志

test:

- 测试结果详见当前目录下 result.txt