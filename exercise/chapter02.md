# ex01

数据集包含 1000 个样本，其中 500 个正例、 500 个反例，将其划分为包含 70% 样本的训练集和 30% 样本的测试集用于留出法评估，估算有多少种划分方式

## Answer

hold-out 方法需要保持数据分布的一致性，所以尽量用 stratified sampling 进行样本划分，即从 500 个正例中选出 350 个正例，从 500 个反例中选出 350 个反例：共 700 个样本作为训练集，其他 300 个样本作为测试集

因此共有 $\left(\begin{matrix}500\\350\end{matrix}\right) * \left(\begin{matrix}500\\350\end{matrix}\right)$ 种划分方式

# ex02

数据集包含 100 个样本，其中正反例各一半，假定学习算法所产生的模型是将新样本预测为训练样本数较多的类别（训练样本数相同时进行随机猜测），试给出用 10 折交叉验证法和留一法分别对错误率进行评估所得的结果

## Answer

10-fold cross validation: 10 折交叉验证由于要保持数据分布的一致性 (西瓜书P26)，因此也采用 stratified sampling 的方法，故每个训练集和测试集都有 10 个正例和 10 个反例。因此模型为随即猜测模型，**期望错误率为 50%**

Leave-one-out: 假定数据集 $D$ 中包含 $m$ 个样本，留一法将其切分为 $m$ 个子集。如果测试集包含 1 个正例，那么训练集有 49 个正例和 50 个反例，预测为反例，错误率 100%，反之错误率也为 100%。综上所述，**LOO 错误率为 100%**

> 验证了《西瓜书》上“LOO 的估计结果未必永远比其他方法准确”的说法

# ex03

若学习器 A 的 F1 值比学习器 B 高，试析 A 的 BEP 值是否也比 B 高

## Answer

首先给出 $F1$ 和 $BEP (Break-Even Point, 平衡点)$ 的定义：

F1 的定义：

$$
F1 = \frac{2 * Precision * Recall}{Precision + Recall}
$$

BEP 的定义：

$$
BEP = Precision = Recall
$$

即 BEP 是 P-R Curve 上 Precision = Recall 时的取值

由二者的定义可知，给定一个 P-R Curve，F1 可能有很多值，因为 threshold 可以有多个取法，但是一个 P-R Curve 只可能有一个 BEP，即 P-R Curve 上 Precision = Recall 时的取值

因此可以给出这样一个反例：假定学习器 A 和学习器 B 的 P-R Curve 完全相同，故二者的 BEP 值相同，取 P-R Curve 上学习器 A 的 F1 比 学习器 B 的 F1 高的点，论证了题目的假设“若学习器 A 的 F1 值比学习器 B 高”，但此时 $BEP_{A} = BEP_{B}$，因此题目不成立

# ex04

试述真正例率（TPR）、假正例率（FPR）与查准率（P）、查全率（R）之间的联系

## Answer

给出四者的定义：

$Precision = (TP)/(TP + FP)$ 即**预测为正例的样本中有多少是真的正例**

$Recall = (TP)/(TP + FN)$ 即**所有为正例的样本中有多少被预测为正例了**

$TPR = (TP)/(TP + FN)$ 与 Recall 同理

$FPR = (FP)/(TN + FP)$ 即**所有为反例的样本中有多少被预测为正例了**

四者之间的联系：

四者之间没有太大联系，唯一的联系是：$Recall$ 与 $TPR$ 的定义是相同的

# ex05

试证明 (2.22) $AUC = 1 − \ell_{\mathrm{rank}}$

## Answer

# ex06

试述错误率和 ROC 曲线的联系

## Answer

# ex07

试证明任意一条 ROC 曲线都有一条代价曲线与之对应，反之亦然

## Answer

# ex08

Min-max 规范化和 z-score 规范化是两种常用的规范化方法。令 $x$ 和 $x^{\prime}$ 分别表示变量在规范化前后的取值，相应的，令 $x_{min}$ 和 $x_{max}$ 表示规范化前的最小值和最大值，$x_{min}^{\prime}$ 和 $x_{max}^{\prime}$ 表示规范化后的最小值和最大值，$\bar{x}$ 和 $\sigma_{x}$ 分别表示规范化前的均值和标准差，则 min-max 规范化、z-score 规范化分别如式 (2.43) 和 (2.44) 所示，试析二者的优缺点

$$
{x'=x_{min}^{\prime}+\frac{x-x_{min}}{x_{max}-x_{min}}~\times(x_{max}^{\prime}~-x_{min}^{\prime})}\quad(2.43)
$$

$$
{x'=\frac{x-\bar{x}}{\sigma_x}}\quad(2.44)
$$

## Answer

# ex09

简述 $ \chi^{2} $ 的检验过程

## Answer

# ex10

试述 Friedman 检验中使用式（2.34）和（2.35）的区别。

## Answer