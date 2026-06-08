# Report Tables

## Stratified split

| split   |   total |   benign |   malignant |   normal |   benign_pct |   malignant_pct |   normal_pct |
|:--------|--------:|---------:|------------:|---------:|-------------:|----------------:|-------------:|
| train   |     546 |      306 |         147 |       93 |         56   |            26.9 |         17   |
| val     |     117 |       65 |          32 |       20 |         55.6 |            27.4 |         17.1 |
| test    |     117 |       66 |          31 |       20 |         56.4 |            26.5 |         17.1 |


## Main model comparison

| Model                         |   Threshold |   Overall Dice |   Lesion Dice |   Normal Dice |   Overall IoU |   Lesion IoU |   Precision |   Recall |    HD95 |   Cls Acc |   Macro F1 |   Macro AUC |
|:------------------------------|------------:|---------------:|--------------:|--------------:|--------------:|-------------:|------------:|---------:|--------:|----------:|-----------:|------------:|
| U-Net MT Pretrained           |         0.5 |       0.808928 |      0.779841 |          0.95 |      0.742136 |     0.699277 |    0.861441 | 0.795368 | 22.6711 |  0.854701 |   0.851961 |    0.945816 |
| U-Net MT Scratch              |         0.5 |       0.778789 |      0.753798 |          0.9  |      0.71438  |     0.676108 |    0.843394 | 0.755667 | 23.5504 |  0.854701 |   0.842461 |    0.947861 |
| Attention U-Net MT Pretrained |         0.5 |       0.755963 |      0.78812  |          0.6  |      0.687016 |     0.704958 |    0.751969 | 0.792012 | 23.9013 |  0.74359  |   0.687222 |    0.902836 |
| Attention U-Net MT Scratch    |         0.5 |       0.743798 |      0.73221  |          0.8  |      0.682405 |     0.658158 |    0.772766 | 0.74811  | 29.8912 |  0.777778 |   0.75842  |    0.945124 |


## Post-processing ablation

| Model                         |   None |   + Largest component |   + Suppression |   Both |
|:------------------------------|-------:|----------------------:|----------------:|-------:|
| U-Net MT Scratch              | 0.7708 |                0.7689 |          0.7806 | 0.7788 |
| Attention U-Net MT Scratch    | 0.7401 |                0.7396 |          0.7443 | 0.7438 |
| U-Net MT Pretrained           | 0.7863 |                0.7833 |          0.8119 | 0.8089 |
| Attention U-Net MT Pretrained | 0.7399 |                0.7478 |          0.748  | 0.756  |


## Pairwise Dice statistics

| Model A                    | Model B                       |   Mean Dice A |   Mean Dice B |   Mean Diff B-A |   Paired t p |   Wilcoxon p |   Cohen dz |
|:---------------------------|:------------------------------|--------------:|--------------:|----------------:|-------------:|-------------:|-----------:|
| U-Net MT Scratch           | Attention U-Net MT Scratch    |      0.778789 |      0.743798 |       -0.034991 |     0.112146 |     0.537171 |  -0.147992 |
| U-Net MT Scratch           | U-Net MT Pretrained           |      0.778789 |      0.808928 |        0.030139 |     0.195757 |     0.178968 |   0.120299 |
| U-Net MT Scratch           | Attention U-Net MT Pretrained |      0.778789 |      0.755963 |       -0.022827 |     0.419041 |     0.757487 |  -0.074975 |
| Attention U-Net MT Scratch | U-Net MT Pretrained           |      0.743798 |      0.808928 |        0.06513  |     0.001537 |     0.087307 |   0.299966 |
| Attention U-Net MT Scratch | Attention U-Net MT Pretrained |      0.743798 |      0.755963 |        0.012165 |     0.627389 |     0.682593 |   0.044995 |
| U-Net MT Pretrained        | Attention U-Net MT Pretrained |      0.808928 |      0.755963 |       -0.052966 |     0.031866 |     0.199306 |  -0.200831 |