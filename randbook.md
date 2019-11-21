# 曲线拟合

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
