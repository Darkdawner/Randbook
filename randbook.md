### B-样条曲线：

基本公式
$$
C(u)=\sum^{n}_{i=0}N_{i,p}(u)P_{i}\\
$$
Cox-de Boor递归公式：
$$
\left\{\begin{aligned}
N_{i,0} &= 
\left\{\begin{aligned}
&1,\quad if\quad u_{i}\leq u\leq u_{i+1}\\
&0, \quad otherwise
\end{aligned}\right.\\
N_{i,p}(u) &= \frac{u-u_{i}}{u_{i+p}-u_{i}}N_{i,p-1}(u)+\frac{u_{i+p+1}-u}{u_{i+p+1}-u_{i+1}}N_{i+1,p-1}(u)
\end{aligned}\right.
$$


# FPN（特征金字塔）

### Feature Pyramid Network：

<img src=".\img\FPN.png" alt="FPN" style="zoom:80%;" />

### 优点：

采用top-down结构抓取到高层语义整体信息，并采用lateral connections融合高层语义信息与低层的细节信息，鲁棒性高，整体相较于图像金字塔而言计算量更小。

# Residual Network

### Introduction

![residual_block](.\img\residual_block.png)

We consider a building block deﬁned as: 
$$
y=F(x,\{W_{i}\})+x
$$
Here x and y are the input and output vectors of the layers considered. The dimensions of ***x*** and ***F*** must be equal. If this is not the case (e.g., when changing the input/output channels), we can perform a linear projection ***Ws*** by the shortcut connections to match the dimensions: 
$$
y=F(x, \{W_{i}\})+W_{s}x
$$

##### <u>Residual Network works for training very deep network !!!</u>

### Example

![residual_example](.\img\residual_example.png)

# **Human Pose Estimation通用评估指标**

需要评估指标来衡量人体姿势估计模型的性能。

**正确部位的百分比 - PCP：**如果两个预测的关节位置与真实肢体关节位置之间的距离小于肢体长度的一半（通常表示为PCP@0.5），则认为肢体被检测到（正确的部位）。

- 它测量肢体的检出率。结果是，由于较短的肢体具有较小的阈值，因此它会对较短的肢体进行惩罚。
- PCP越高，模型越好。

**正确关键点的百分比 - PCK：**如果预测关节与真实关节之间的距离在特定阈值内，则检测到的关节被认为是*正确*的。阈值可以是：

- PCKh@0.5是阈值=头骨链接的50％时
- PCK@0.2 ==预测和真实关节之间的距离<0.2 *躯干直径
- 有时将150 mm作为阈值。
- 缓解较短的肢体问题，因为较短的肢体具有较小的躯干和头骨连接。
- PCK用于2D和3D（PCK3D）。再次，越高越好。

**检测到的关节的百分比 - PDJ：**如果预测关节和真实关节之间的距离在躯干直径的某一部分内，则检测到的关节被认为是正确的。PDJ@0.2 =预测和真实关节之间的距离<0.2 *躯干直径。

**基于对象关键点相似度（OKS）的mAP：**

- 常用于COCO关键点的挑战。
- ![img](C:\Users\刘晟\Desktop\randbook\img\OKS.png)
