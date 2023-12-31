# 原来的分类结果

第一次

- Model saved: GB-local-2023-05-31-18-19-56.pkl

- Model saved: embedding-2023-05-31-18-19-56.pkl

- Model loaded: GB-local-2023-05-31-18-19-56.pkl

- Model loaded: embedding-2023-05-31-18-19-56.pkl
  testing result:

- Precision: [0.81191223 0.76344086 0.91091314]

- Recall:    [0.71944444 0.83858268 0.8930131 ]

- F-measure: [0.7628866  0.79924953 0.90187431]

- Accuracy:  0.8250377073906485

- Classification Report:
      precision    recall  f1-score   support

  negative     0.8119    0.7194    0.7629       360
   neutral     0.7634    0.8386    0.7992       508
  positive     0.9109    0.8930    0.9019       458

  accuracy                         0.8250      1326
  macro avg     0.8288    0.8170    0.8213      1326
         weighted avg     0.8275    0.8250    0.8248      1326

第二次

- Model saved: GB-local-2023-05-31-18-52-01.pkl

- Model saved: embedding-2023-05-31-18-52-01.pkl

- Model loaded: GB-local-2023-05-31-18-52-01.pkl

- Model loaded: embedding-2023-05-31-18-52-01.pkl
  testing result:

- Precision: [0.815625   0.76978417 0.91111111]

- Recall:    [0.725      0.84251969 0.89519651]

- F-measure: [0.76764706 0.80451128 0.9030837 ]

- Accuracy:  0.8288084464555053

- Classification Report:
      precision    recall  f1-score   support

  negative     0.8156    0.7250    0.7676       360
   neutral     0.7698    0.8425    0.8045       508
  positive     0.9111    0.8952    0.9031       458

  accuracy                         0.8288      1326
  macro avg     0.8322    0.8209    0.8251      1326
         weighted avg     0.8310    0.8288    0.8285      1326

# 加上替换专有词和实体词

- Model saved: GB-local-2023-05-31-18-28-25.pkl

- Model saved: embedding-2023-05-31-18-28-25.pkl

- Model loaded: GB-local-2023-05-31-18-28-25.pkl

- Model loaded: embedding-2023-05-31-18-28-25.pkl
  testing result:

- Precision: [0.82142857 0.7486911  0.90786517]

- Recall:    [0.70277778 0.84448819 0.88209607]

- F-measure: [0.75748503 0.79370953 0.89479513]

- Accuracy:  0.8190045248868778

- Classification Report:
      precision    recall  f1-score   support

  negative     0.8214    0.7028    0.7575       360
   neutral     0.7487    0.8445    0.7937       508
  positive     0.9079    0.8821    0.8948       458

  accuracy                         0.8190      1326
  macro avg     0.8260    0.8098    0.8153      1326
         weighted avg     0.8234    0.8190    0.8188      1326

# 加上 domain specific

- Model saved: GB-local-2023-05-31-18-31-22.pkl

- Model saved: embedding-2023-05-31-18-31-22.pkl

- Model loaded: GB-local-2023-05-31-18-31-22.pkl

- Model loaded: embedding-2023-05-31-18-31-22.pkl
  testing result:

- Precision: [0.82428115 0.76106195 0.91071429]

- Recall:    [0.71666667 0.84645669 0.89082969]

- F-measure: [0.7667162  0.80149115 0.90066225]

- Accuracy:  0.8265460030165912

- Classification Report:
      precision    recall  f1-score   support

  negative     0.8243    0.7167    0.7667       360
   neutral     0.7611    0.8465    0.8015       508
  positive     0.9107    0.8908    0.9007       458

  accuracy                         0.8265      1326
  macro avg     0.8320    0.8180    0.8230      1326
         weighted avg     0.8299    0.8265    0.8263      1326

# 加上斜体 大写

第一次

- Model saved: GB-local-2023-05-31-18-33-59.pkl

- Model saved: embedding-2023-05-31-18-33-59.pkl

- Model loaded: GB-local-2023-05-31-18-33-59.pkl

- Model loaded: embedding-2023-05-31-18-33-59.pkl
  testing result:

- Precision: [0.81987578 0.76523297 0.91255605]

- Recall:    [0.73333333 0.84055118 0.88864629]

- F-measure: [0.77419355 0.8011257  0.90044248]

- Accuracy:  0.8280542986425339

- Classification Report:
      precision    recall  f1-score   support

  negative     0.8199    0.7333    0.7742       360
   neutral     0.7652    0.8406    0.8011       508
  positive     0.9126    0.8886    0.9004       458

  accuracy                         0.8281      1326
  macro avg     0.8326    0.8208    0.8253      1326
         weighted avg     0.8310    0.8281    0.8281      1326

第二次

- Model saved: GB-local-2023-05-31-18-45-57.pkl

- Model saved: embedding-2023-05-31-18-45-57.pkl

- Model loaded: GB-local-2023-05-31-18-45-57.pkl

- Model loaded: embedding-2023-05-31-18-45-57.pkl
  testing result:

- Precision: [0.8136646  0.76523297 0.9103139 ]

- Recall:    [0.72777778 0.84055118 0.88646288]

- F-measure: [0.76832845 0.8011257  0.89823009]

- Accuracy:  0.8257918552036199

- Classification Report:
      precision    recall  f1-score   support

  negative     0.8137    0.7278    0.7683       360
   neutral     0.7652    0.8406    0.8011       508
  positive     0.9103    0.8865    0.8982       458

  accuracy                         0.8258      1326
  macro avg     0.8297    0.8183    0.8226      1326
  weighted avg     0.8285    0.8258    0.8258      1326

# 加上处理领域特定单词，处理斜体、大写

第一次

- Model saved: GB-local-2023-05-31-18-36-01.pkl

- Model saved: embedding-2023-05-31-18-36-01.pkl

- Model loaded: GB-local-2023-05-31-18-36-01.pkl

- Model loaded: embedding-2023-05-31-18-36-01.pkl
  testing result:

- Precision: [0.81931464 0.76207513 0.91255605]

- Recall:    [0.73055556 0.83858268 0.88864629]

- F-measure: [0.77239354 0.79850047 0.90044248]

- Accuracy:  0.8265460030165912

- Classification Report:
      precision    recall  f1-score   support

  negative     0.8193    0.7306    0.7724       360
   neutral     0.7621    0.8386    0.7985       508
  positive     0.9126    0.8886    0.9004       458

  accuracy                         0.8265      1326
  macro avg     0.8313    0.8193    0.8238      1326
         weighted avg     0.8296    0.8265    0.8266      1326

第二次

- Model saved: GB-local-2023-05-31-18-49-37.pkl

- Model saved: embedding-2023-05-31-18-49-37.pkl

- Model loaded: GB-local-2023-05-31-18-49-37.pkl

- Model loaded: embedding-2023-05-31-18-49-37.pkl
  testing result:

- Precision: [0.82075472 0.7633452  0.90807175]

- Recall:    [0.725      0.84448819 0.88427948]

- F-measure: [0.7699115  0.80186916 0.8960177 ]

- Accuracy:  0.8257918552036199

- Classification Report:
      precision    recall  f1-score   support

  negative     0.8208    0.7250    0.7699       360
   neutral     0.7633    0.8445    0.8019       508
  positive     0.9081    0.8843    0.8960       458

  accuracy                         0.8258      1326
  macro avg     0.8307    0.8179    0.8226      1326
         weighted avg     0.8289    0.8258    0.8257      1326

# 只处理斜体

- Model saved: GB-local-2023-05-31-18-41-42.pkl

- Model saved: embedding-2023-05-31-18-41-42.pkl

- Model loaded: GB-local-2023-05-31-18-41-42.pkl

- Model loaded: embedding-2023-05-31-18-41-42.pkl
  testing result:

- Precision: [0.8125    0.7625    0.9103139]

- Recall:    [0.72222222 0.84055118 0.88646288]

- F-measure: [0.76470588 0.79962547 0.89823009]

- Accuracy:  0.8242835595776772

- Classification Report:
      precision    recall  f1-score   support

  negative     0.8125    0.7222    0.7647       360
   neutral     0.7625    0.8406    0.7996       508
  positive     0.9103    0.8865    0.8982       458

  accuracy                         0.8243      1326
  macro avg     0.8284    0.8164    0.8209      1326
         weighted avg     0.8271    0.8243    0.8242      1326

# 只处理大写

- Model saved: GB-local-2023-05-31-18-43-52.pkl

- Model saved: embedding-2023-05-31-18-43-52.pkl

- Model loaded: GB-local-2023-05-31-18-43-52.pkl

- Model loaded: embedding-2023-05-31-18-43-52.pkl
  testing result:

- Precision: [0.82747604 0.75929204 0.90848214]

- Recall:    [0.71944444 0.84448819 0.88864629]

- F-measure: [0.76968796 0.79962721 0.89845475]

- Accuracy:  0.8257918552036199

- Classification Report:
      precision    recall  f1-score   support

  negative     0.8275    0.7194    0.7697       360
   neutral     0.7593    0.8445    0.7996       508
  positive     0.9085    0.8886    0.8985       458

  accuracy                         0.8258      1326
  macro avg     0.8318    0.8175    0.8226      1326
         weighted avg     0.8293    0.8258    0.8256      1326