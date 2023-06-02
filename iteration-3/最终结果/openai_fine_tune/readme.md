model:

- 该模型为私人 OpenAI 账号通过 API_KEY 使用 Fine-Tune 服务微调 Curie 模型得到（助教可能难以访问到）
- 模型名称：curie:ft-personal-2023-05-30-03-33-28
- 训练方法：将训练集进行格式转换得到用于模型微调的数据集（.JSONL 文件），格式如下：{"prompt": "<text>", "completion": "<label>"}
- 调用方法：openai api completions.create -m curie:ft-personal-2023-05-30-03-33-28 -p <TEXT>，或以 Python 代码的方式调用（详见 analyzer.py 中的 OpenAIEnd2EndAnalyzer 类）

train:

- openai api fine_tunes.create -t ./dataset/fine_tune_set.jsonl -m curie

test:

- 测试结果详见当前目录下 result.txt
