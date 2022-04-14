# GO-ICP: A Globally Optimal Solution to 3D ICP Point-Set Registration--TPAMI'16
## 简介
使用分支定界和传统ICP相结合，分支定界搜索优化的解，ICP对解进行细化并将结果作为新的界限进行搜索，直到算法收敛。
## 分支界限法
将该算法推广到3D registration有两个困难：1)如何将3D变换参数化和确定分支域，2)如何高效地寻找上下界。
### 域参数化
在使用轴角表示法的情况下，每个旋转都可以用一个3D向量$v$来表示，轴是$\frac{v}{\|v\|}$，角是$\|v\|$，$R_r$作为旋转矩阵，可以被计算为
$R_r=\exp([r]_{\times})=I+\frac{[r]_{\times}\sin{\|r\|}}{\|r\|}+\frac{[r]_{\times}^2(1-\cos{\|r\|})}{\|r\|^2}$
$[\cdot]_{\times}$是斜对称矩阵
$[r]_{\times}=\begin{bmatrix}0&-r_3&r_2\\r_3&0&-r_1\\-r_2&r_1&0\end{bmatrix}=\log{R_r}=\frac{\|r\|}{2\sin{\|r\|}}(R_r-R_r^T), \|r\|=\arccos((\mathrm{trace}(R_r)-1)/2)$
# comment
看不明白，太难了，但是根据其他几篇论文来看，这个方法准确性和计算开销都不如FGR