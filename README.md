# depth-estimation-paper-note

## 各任务评价标准

<img src="./images/evaluate.png" style="zoom: 50%;" />

## Benchmark

- Depth Evaluation

  |      | Abs Rel | Sq Rel | RMSE | RMSE Log |$\delta_{t} < 1.25$      | $\delta_{t} < 1.25$ | $\delta_{t} < 1.25$ |
  | ---- | :-----: | :----: | :--: | :------: | :--: | :--: | ---- |
  |      |         |        |      |          |      |      |      |
  |      |         |        |      |          |      |      |      |
  |      |         |        |      |          |      |      |      |
  |      |         |        |      |          |      |      |      |

- Disparity Evaluation

- Flow Evaluation

- Pose Evaluation

## 1. Monocular + Self-supervised

## 2. Monocular + Supervised
## 3. Binocular + Self-supervised
## 4. Binocular + Supervised

### (1)Group-wise Correlation Stereo Network(GwcNet)

结合了目前的两种代价聚合的方法

correlation-based

<img src="./images/Gwcnet_3.png" style="zoom: 50%;" />

concatenation-based

<img src="./images/Gwcnet_4.png" style="zoom:50%;" />

作者在论文中指出， 使用correlation-based的方法进行代价聚合，由于最后对于不同的视差d只会生成单通道的特征图，这样虽然比较efficient，但是丢失了太多的信息；而对于concatenation-based的方法，由于生成的volume里面并不包括特征相似性的信息，所以需要在aggregation的部分从头开始学习相似性的评价，因此需要更多的参数，导致效率不高。

因此作者提出了，基于分组思想的Group-wise correlation network。

![](./images/Gwcnet_1.png)

其中，group-wise correlation的思想如下：

<img src="./images/Gwcnet_5.png" style="zoom:50%;" />

这样就相当于给出了$N_{g}$个代价体。作者认为这种方式能够在给出特征相似性的同时，保留更多的信息。同时作者还指出，该文所提出的方法能够与concatenation volume同时使用。![image-20200727215020902](/home/cy/.config/Typora/typora-user-images/image-20200727215020902.png)

