# Pretrained-CNN

This project focuses on the predictive power of a CNN on Medical (Chest X-ray images) dataset to accurately classify an image as normal or not. This is part of a larger project which combines CNN and LLM to learn from images and the corresponding medical reports of the same patient to make highly accurate binary classification. In this project, only the classification layer was trained. This project serves as a baseline for comparing CNN+LLM.

## Data

Indiana University Chest X-ray dataset was used in the project.
The dataset contains 7,470 pairs of images and reports and measures 14.19 GB. The reports were used as ground truth to compare CNN's predictions.
IU X-ray (Demner-Fushman et al., 2016) can be accessed [here](https://www.kaggle.com/datasets/raddar/chest-xrays-indiana-university)

## CNN Model

The architecture of EfficientNet-B1 is used to process and convert the images into vector embeddings. EfficientNet-B1 is a Depp CNN pretrained on Medical dataset (ImageNet) and has ~6.5 Million trainable parameters. EfficientNet‑B1 component remains frozen. I've leveraged pre‑trained knowledge from the CNN model but only updated the classification layer during training. It's been proven that EfficientNet architecture gives slightly better accuracy per parameter. Refer to the research paper [here](https://arxiv.org/pdf/1905.11946)

## Classification Layer

Transfer Learning is used to avoid overfitting by freezing the backbone of the CNN. The model uses pre-trained Conv Layers as a fixed feature extractor. Only the classification layer is trained. 

## Parameters

| Parameters | Specification |
| --- | --- |
| Optimizer | Adam |
| Loss Function | Cross Entropy |
| Trainable Parameters | 2562 |
| Learning Rate | 0.003 |
| Number of Epochs | 40 |
| Train / Test data ratio | 80 : 20 |

## Results

| Epoch | Phase | Loss   | Accuracy | Precision | Recall | F1-Score |
|-------|-------|--------|----------|-----------|--------|----------|
| 1     | Train | 0.6296 | 0.6517   | 0.6860    | 0.8376 | 0.7543   |
|       | Val   | 0.6047 | 0.6680   | 0.7427    | 0.7396 | 0.7411   |
| 2     | Train | 0.6209 | 0.6606   | 0.7035    | 0.8092 | 0.7527   |
|       | Val   | 0.5882 | 0.6921   | 0.7159    | 0.8635 | 0.7828   |
| 3     | Train | 0.6117 | 0.6685   | 0.7107    | 0.8103 | 0.7572   |
|       | Val   | 0.5997 | 0.6760   | 0.7537    | 0.7365 | 0.7450   |
| 4     | Train | 0.6172 | 0.6668   | 0.7093    | 0.8098 | 0.7562   |
|       | Val   | 0.5908 | 0.6814   | 0.7224    | 0.8187 | 0.7676   |
| 5     | Train | 0.6128 | 0.6691   | 0.7104    | 0.8129 | 0.7582   |
|       | Val   | 0.6476 | 0.6573   | 0.7979    | 0.6250 | 0.7009   |
| 6     | Train | 0.6072 | 0.6746   | 0.7163    | 0.8116 | 0.7610   |
|       | Val   | 0.6139 | 0.6760   | 0.7692    | 0.7083 | 0.7375   |
| 7     | Train | 0.6075 | 0.6775   | 0.7169    | 0.8174 | 0.7639   |
|       | Val   | 0.6024 | 0.6700   | 0.7395    | 0.7510 | 0.7452   |
| 8     | Train | 0.6125 | 0.6715   | 0.7147    | 0.8077 | 0.7583   |
|       | Val   | 0.6085 | 0.6774   | 0.7500    | 0.7469 | 0.7484   |
| 9     | Train | 0.6134 | 0.6743   | 0.7174    | 0.8079 | 0.7600   |
|       | Val   | 0.6076 | 0.6707   | 0.7246    | 0.7865 | 0.7542   |
| 10    | Train | 0.6116 | 0.6680   | 0.7127    | 0.8037 | 0.7555   |
|       | Val   | 0.6095 | 0.6700   | 0.7580    | 0.7146 | 0.7357   |
| 11    | Train | 0.6130 | 0.6807   | 0.7221    | 0.8121 | 0.7645   |
|       | Val   | 0.6081 | 0.6673   | 0.7327    | 0.7594 | 0.7458   |
| 12    | Train | 0.6056 | 0.6772   | 0.7192    | 0.8105 | 0.7622   |
|       | Val   | 0.6441 | 0.6426   | 0.7689    | 0.6344 | 0.6952   |
| 13    | Train | 0.6095 | 0.6765   | 0.7181    | 0.8116 | 0.7620   |
|       | Val   | 0.6110 | 0.6747   | 0.7418    | 0.7573 | 0.7495   |
| 14    | Train | 0.6081 | 0.6700   | 0.7123    | 0.8100 | 0.7580   |
|       | Val   | 0.6070 | 0.6653   | 0.7431    | 0.7323 | 0.7377   |
| 15    | Train | 0.6129 | 0.6735   | 0.7163    | 0.8084 | 0.7596   |
|       | Val   | 0.6002 | 0.6780   | 0.7129    | 0.8354 | 0.7693   |
| 16    | Train | 0.6145 | 0.6748   | 0.7158    | 0.8134 | 0.7615   |
|       | Val   | 0.6089 | 0.6754   | 0.7540    | 0.7344 | 0.7441   |
| 17    | Train | 0.6170 | 0.6768   | 0.7186    | 0.8113 | 0.7621   |
|       | Val   | 0.5936 | 0.6834   | 0.7282    | 0.8094 | 0.7667   |
| 18    | Train | 0.6126 | 0.6733   | 0.7152    | 0.8111 | 0.7601   |
|       | Val   | 0.5938 | 0.6894   | 0.7091    | 0.8760 | 0.7838   |
| 19    | Train | 0.6133 | 0.6748   | 0.7148    | 0.8161 | 0.7621   |
|       | Val   | 0.5940 | 0.6801   | 0.7429    | 0.7677 | 0.7551   |
| 20    | Train | 0.6060 | 0.6857   | 0.7247    | 0.8184 | 0.7687   |
|       | Val   | 0.6129 | 0.6747   | 0.7599    | 0.7219 | 0.7404   |
| 21    | Train | 0.6167 | 0.6730   | 0.7152    | 0.8100 | 0.7597   |
|       | Val   | 0.6242 | 0.6586   | 0.7563    | 0.6917 | 0.7225   |
| 22    | Train | 0.6085 | 0.6738   | 0.7158    | 0.8108 | 0.7603   |
|       | Val   | 0.6134 | 0.6707   | 0.7653    | 0.7031 | 0.7329   |
| 23    | Train | 0.6108 | 0.6716   | 0.7144    | 0.8087 | 0.7586   |
|       | Val   | 0.6294 | 0.6533   | 0.7558    | 0.6802 | 0.7160   |
| 24    | Train | 0.6200 | 0.6713   | 0.7121    | 0.8140 | 0.7596   |
|       | Val   | 0.6025 | 0.6747   | 0.7554    | 0.7302 | 0.7426   |
| 25    | Train | 0.6055 | 0.6864   | 0.7245    | 0.8205 | 0.7695   |
|       | Val   | 0.5934 | 0.6760   | 0.7179    | 0.8167 | 0.7641   |
| 26    | Train | 0.6081 | 0.6807   | 0.7191    | 0.8200 | 0.7662   |
|       | Val   | 0.6076 | 0.6707   | 0.6973    | 0.8615 | 0.7707   |
| 27    | Train | 0.6033 | 0.6817   | 0.7239    | 0.8103 | 0.7646   |
|       | Val   | 0.6116 | 0.6680   | 0.7549    | 0.7156 | 0.7348   |
| 28    | Train | 0.6087 | 0.6785   | 0.7197    | 0.8126 | 0.7634   |
|       | Val   | 0.6351 | 0.6546   | 0.7768    | 0.6490 | 0.7072   |
| 29    | Train | 0.6234 | 0.6648   | 0.7115    | 0.7985 | 0.7525   |
|       | Val   | 0.5973 | 0.6780   | 0.7503    | 0.7479 | 0.7491   |
| 30    | Train | 0.5988 | 0.6803   | 0.7212    | 0.8137 | 0.7646   |
|       | Val   | 0.5921 | 0.6814   | 0.7345    | 0.7896 | 0.7610   |
| 31    | Train | 0.6098 | 0.6782   | 0.7157    | 0.8224 | 0.7653   |
|       | Val   | 0.5931 | 0.6948   | 0.7329    | 0.8260 | 0.7767   |
| 32    | Train | 0.6055 | 0.6795   | 0.7211    | 0.8116 | 0.7637   |
|       | Val   | 0.6118 | 0.6740   | 0.7471    | 0.7448 | 0.7460   |
| 33    | Train | 0.6140 | 0.6792   | 0.7212    | 0.8105 | 0.7633   |
|       | Val   | 0.5981 | 0.6827   | 0.7102    | 0.8552 | 0.7760   |
| 34    | Train | 0.6063 | 0.6775   | 0.7188    | 0.8124 | 0.7627   |
|       | Val   | 0.6003 | 0.6867   | 0.7316    | 0.8094 | 0.7685   |
| 35    | Train | 0.6167 | 0.6767   | 0.7174    | 0.8140 | 0.7626   |
|       | Val   | 0.6014 | 0.6720   | 0.7251    | 0.7885 | 0.7555   |
| 36    | Train | 0.6044 | 0.6792   | 0.7203    | 0.8129 | 0.7638   |
|       | Val   | 0.5955 | 0.6941   | 0.7244    | 0.8458 | 0.7804   |
| 37    | Train | 0.6120 | 0.6777   | 0.7194    | 0.8113 | 0.7626   |
|       | Val   | 0.6281 | 0.6580   | 0.7702    | 0.6667 | 0.7147   |
| 38    | Train | 0.6155 | 0.6716   | 0.7142    | 0.8092 | 0.7588   |
|       | Val   | 0.6034 | 0.6861   | 0.7061    | 0.8760 | 0.7820   |
| 39    | Train | 0.6008 | 0.6885   | 0.7279    | 0.8176 | 0.7701   |
|       | Val   | 0.6159 | 0.6660   | 0.7497    | 0.7208 | 0.7350   |
| 40    | Train | 0.6050 | 0.6808   | 0.7210    | 0.8153 | 0.7653   |
|       | Val   | 0.5950 | 0.6774   | 0.7281    | 0.7948 | 0.7600   |

## Conclusion

![Training Metrics](frozen_training_validation_metrics.png)

The model didn't show remarkable performance but was neither underfitted nor overfitted.
