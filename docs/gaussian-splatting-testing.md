# 3D-GS实验结果


## 3D-GS实验结果表格

|               Metrics\Dataset                | DrJohnson | Playroom |  Train  |  Truck  |
| :------------------------------------------: | :-------: | :------: | :-----: | :-----: |
|             Train L1 (Iter 7000)             |  0.0187   |  0.0156  | 0.0548  | 0.0343  |
|            Train L1 (Iter 30000)             |  0.0088   |  0.0107  | 0.0285  | 0.0235  |
|             Test L1 (Iter 7000)              |  0.0264   |  0.214   | 0.0796  | 0.0384  |
|             Test L1 (Iter 30000)             |  0.0212   |  0.211   | 0.0576  | 0.0308  |
|            Train PSNR (Iter 7000)            |   29.72   |  31.91   |  21.48  |  24.80  |
|           Train PSNR (Iter 30000)            |   36.95   |  36.10   |  26.76  |  27.37  |
|            Test PSNR (Iter 7000)             |   27.07   |  29.64   |  19.42  |  23.88  |
|            Test PSNR (Iter 30000)            |   29.18   |  30.16   |  21.91  |  25.34  |
|            Test SSIM (Iter 30000)            |   0.898   |  0.901   |  0.811  |  0.878  |
|           Test LPIPS (Iter 30000)            |   0.247   |  0.247   |  0.210  |  0.148  |
|       Training Time Cost/s (Iter 7000)       |  4m 15s   |  3m 33s  | 2m 14s  | 2m 57s  |
|      Training Time Cost/s (Iter 30000)       |  27m 19s  | 21m 25s  | 12m 18s | 17m 50s |
|      Number of points at initialisation      |   80861   |  37005   | 182686  | 136029  |
|   Peak GPU Memory Allocated/GB (Training)    |   8.955   |  6.451   |  3.617  |  5.550  |
|   Peak GPU Memory Allocated/GB (Rendering)   |   8.383   |  6.296   |  3.995  |  4.158  |
| Frames per Second (Rendering, No Img Saving) |    110    |   156    |   201   |   148   |

