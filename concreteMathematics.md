# 递归问题

## 热身题

1. $n=2$时不满足，因为中间集合$\{2 \cdots n-1\}$无意义。
2. 记最少移动次数为$T_{n}$，易得$T_{0}=0，T_{1}=2$。将n个盘子从A移动到B最简步骤有：
   
    1. 将n-1个盘子从A移动到B
    2. 将第n个盘子从A移动到中间的桩子C
    3. 将n-1个盘子从B移动到A，这一步与第一步完全对称
    4. 将第n个盘子从C移动到B
    5. 将n-1个盘子从A移动到B
    
    可得$T_{n}=3T_{n-1}+2$，易得递推关系：
    $$
    \begin{align*}
     T_{n}&=3T_{n-1}+2 \\
     T_{0}&=0
    \end{align*}
    $$
    其闭合式为$T_{n}=3^{n}-1$，由数学归纳法轻易可证。
3. $T_n=3^n-1$，即n个盘子在3个桩子上的全排列。则在移动序列中会遇到n个圆盘的每一种情况。
4. 不是。因为对于移动第$k$个盘子(最简移动步数记为$S_k$)，最简分为以下三步:

    1. 将其上的盘子移动到不影响的位置，最多移动$k-1$个盘子。
    2. 将这个盘子移到到目标桩子上，只需$1$步。
    
    由于这对所有的合法的$k$都成立，故$S_n \le 2^n-1$
5. 不可以。为达到所求效果，需在所示图中作一圆D，将8个区域都划分为D内和D外两个部分,则需穿过每个区域的边界两次，考虑边界重合的情况下，至少需要穿过7个边界。而两个圆只有两个交点，故最多只能穿过6个边界。
6. 一条直线使平面增加$k$个封闭区域，当且仅当这条直线被分为$k+2$段。故已有$n-1$条直线时$k$最多有$k=n-2$，可得$n$条直线最多形成封闭区域的数量$C_n$满足
    $$
    C_n=\left\{\begin{matrix}
    0,&n=1,2 \\
    C_{n-1}+n-2,&n>2
    \end{matrix}\right.
    $$
    整理得$C_n=\frac{(n-1)(n-2)}{2}, n\ge 1$
7. 只有递归步骤而无递归边界，如$H(1)=J(2)-J(1)=0$

## 作业题

8. 由题：
    $$
    \begin{align*}
        Q_{n}&=\frac{1+\frac{1+Q_{n-2}}{Q_{n-3}}}{Q_{n-2}} \\
            &=\frac{1+\frac{1+Q_{n-3}}{Q_{n-2}}}{Q_{n-3}} \\
            &=\frac{1+Q_{n-4}}{Q_{n-3}}\\
            &=Q_{n-5}，n \geq 5
    \end{align*}
    $$
    故
    $$
    Q_{4k+l}=\varphi_{l} \\
    \begin{align*}
        其中\varphi_{l}=
        \left\{\begin{matrix}
            \alpha,l=0\\
            \beta,l=1\\
            \frac{1+\beta}{\alpha},l=2\\
            \frac{1+\alpha}{\beta},l=3\\
        \end{matrix}\right.
        ，k \in N
    \end{align*}
    $$

9. 
    a. 假设P(n)成真，有：  
    $$
    \begin{align*}
    	x_{1}  \cdots  x_{n}&\le (\frac{x_{1}+  \cdots  +x_{n}}{n})^{n} \\
    	x_{1}  \cdots  x_{n}&\le (\frac{x_{1}+  \cdots  +x_{n-1}+\frac{x_1+  \cdots  +x_{n-1}}{n-1}}{n})^{n} \\
    	x_{1}  \cdots  x_{n}&\le (\frac{(x_{1}+  \cdots  +x_{n-1})\cdot\frac{n}{n-1}}{n})^{n} \\
    	x_{1}  \cdots  x_{n}&\le (\frac{x_{1}+  \cdots  +x_{n-1}}{n-1})^{n} \\
        (x_{1}  \cdots  x_{n-1})\cdot\frac{x_1+  \cdots  +x_{n-1}}{n-1}&\le (\frac{x_{1}+  \cdots  +x_{n}}{n})^{n} \\
        (x_{1}  \cdots  x_{n-1})&\le (\frac{x_{1}+  \cdots  +x_{n}}{n})^{n-1}，即P(n-1) \\
        综上，P(n)\Rightarrow P(n-1) 
    \end{align*}
    $$
    b.
    $$
    \begin{align*}
    引入P(n)，得：x_{1}  \cdots  x_{n}&\le (\frac{x_{1}+  \cdots  +x_{n}}{n})^{n},x_1,  \cdots  ,x_n \ge 0 (1)\\
    代入x_{n+1}  \cdots  x_{2n}得：x_{n+1}  \cdots  x_{2n}&\le (\frac{x_{n+1}+  \cdots  +x_{2n}}{n})^{n},x_{n+1},  \cdots  ,x_{2n} \ge 0 (2) \\
    综合(1)(2)得：x_1  \cdots  x_{2n} &\le (\frac{(x_{1}+  \cdots  +x_{n})*(x_{n+1}+  \cdots  +x_{2n})}{n})^{n}(3) \\
    引入P(2)，得x_1x_2&\le (\frac{x_1+x_2}{2})^{2} \\
    代入x_{1}=x_{1}+  \cdots  +x_{n}和x_2=x_{n+1}+  \cdots  +x_{2n}得：\\
    (x_{1}+  \cdots  +x_{n})\cdot(x_{n+1}+  \cdots  +x_{2n}) &\le (\frac{x_{1}+  \cdots  +x_{n}+x_{n+1}+  \cdots  +x_{2n}}{2})^{2}(4) \\
    综合(3)(4)得:
    x_1  \cdots  x_{2n} &\le (\frac{x_{1}+  \cdots  +x_{2n}}{2n})^{2n}，即P(2n) \\
    故P(2)和P(n)\Rightarrow P(2n)
    \end{align*}
    $$
    c.

    假设$P(n)$成立，同时设 $A_{n-1}=(\frac{a_1+  \cdots  +a_{n-1}}{n-1}),G_{n-1}=\sqrt[n-1]{a_1  \cdots  a_{n-1}}\ $ :
    $$
    将A代入P(n)中x_n得: \\
    (\frac{a_1+  \cdots  +a_{n-1}+A_{n-1}}{n})^n \ge a_1  \cdots  a_{n-1}A_{n-1}
    $$
    又$a_1+  \cdots  +a_{n-1}=(n-1)A_{n-1},\ a_1  \cdots  a_{n-1}=G_{n-1}^{n-1}$，代入得:
    $$
    \begin{align*}
    A_{n-1}^{n}&\ge G_{n-1}^{n-1}\cdot A_{n-1} \\
    A_{n-1}^{n-1}&\ge G_{n-1}^{n-1} \\
    (\frac{a_1+  \cdots  +a_{n-1}}{n-1})^{n-1} &\ge a_1  \cdots  a_{n-1} ,即P(n-1)成立
    \end{align*}
    $$
    即$P(n)\Rightarrow P(n-1)$，又由b，任意的自然数$k$,有$P(2^k)$成立，则$\underset{n \to +\infty}{\lim}P(n)$成立，可得递归式:
    $$
    \begin{matrix}
    P(n) \Rightarrow P(n-1),\; n \ge 2 \; &(1) \\
    \underset{n \to +\infty}{\lim}P(n) \; &(2)
    \end{matrix}
    $$
    则对所有n为正整数的情况下$P(n)$对所有的n为真

10. 记另一桩子为C，将一个有 $n$ 个圆盘的塔从A移动到B，若$n=0$，则$Q_0=0$，若$n>0$可以有以下步骤:
    1. 将前n-1个盘子从A移动到C，花费步数为$R_{n-1}$
    1. 将第n个盘子从A移动到B，花费步数为$1$
    1. 将前n-1个盘子从C移动到B，花费步数为$R_{n-1}$

    每个步骤的最简性不再赘述，故:
    $$
    Q_n=\left\{\begin{matrix}
    0,&n=0 \\
    2R_{n-1}+1,&n>0
    \end{matrix}\right.
    $$
    而将一个有 $n$ 个圆盘的塔从B移动到A，若$n=0$，则$R_0=0$，若$n>0$可以有以下步骤:

     1. 将前n-1个盘子从B移动到A，花费步数为$R_{n-1}$

     2. 将第n个盘子从B移动到C，花费步数为$1$

     3. 将前n-1个盘子从A移动到B，花费步数为$Q_{n-1}$

     4. 将第n个盘子从C移动到A，花费步数为$1$

     5. 将前n-1个盘子从B移动到A，花费步数为$R_{n-1}$

    每个步骤的最简性亦不赘述，故:
    $$
    R_n=\left\{\begin{matrix}
    0,&n=0 \\
    2R_{n-1}+Q_{n-1}+2,&n>0
    \end{matrix}\right.
    $$
    整理得:
    $$
    R_n=\left\{\begin{matrix}
    0,&n=0 \\
    Q_n+Q_{n-1}+1,&n>0
    \end{matrix}\right.
    $$

11. a.
      记移动$n$对盘子步数为$S_n$,显然有$S_0=0$。对于$n$对盘子，欲将其从A桩移动到B桩，则需要三步:

      1. 将前$n-1$对盘子由A移动到另一个桩子C，需要$S_{n-1}$步。
      2. 将最后两个盘子移至B桩，需要2步。
      3. 将前$n-1$对盘子由C移动到B，需要$S_{n-1}$步

      综上，$S_{n} \le 2S_{n-1}+2$。最简性不再赘述，故$S_{n} = 2S_{n-1}+2$。 
      可得封闭式$S_{n}=2 \cdot 2^n-2=2^{n+1}-2$

      b.
      记移动$n(n \ge 0)$对盘子步数为$S^{'}_{n}$，显然$S^{'}_{0}=0$。
      移动$n$对盘子可分为以下几步:

      1. 将前$n-1$对盘子按a中方法由A移动到B上，需要$S_{n-1}$步，此时第$n-1$对盘子内部顺序相反。
      2. 将第$n$对盘子倒序放置在C上，需要2步。
      3. 将前$n-1$对盘子按a中方法由B移动到A上，需要$S_{n-1}$步，此时第$n-1$对盘子内部顺序与开始时相同。
      4. 将第$n$对盘子倒序放置在B上，需要2步，此时它们内部顺序与开始时相同。
      5. 将前$n-1$对盘子讲究顺序地由A移动到B上，需要$S^{'}_{n-1}$步。

      故$S^{'}_{n} \le S^{'}_{n-1}+2S_{n-1}+4$，可证明对$n >1$最简，而$S^{'}_1=3$，$S^{'}_{n} = S^{'}_{n-1}+2S_{n-1}+4=S^{'}_{n-1}+2^{n+1}=2^{n+2}-5$。

12. 与11a类似，有
    $$
    A_n=\left\{\begin{matrix}
      0, &n=0 \\
      2A_{n-1}+m_n, &n >0
      \end{matrix}\right.
    $$
      即
    $$
    A_n=\left\{\begin{matrix}
      0, &n=0 \\
      \sum_{i=1}^{n}{m_i \cdot 2^{n-i}}, &n >0
      \end{matrix}\right.
    $$

13. 与折线情况类似，有
    $$
    ZZ_n=\left\{\begin{matrix}
      1, &n=0 \\
      L_{3n}-5n=4.5n^2-3.5n+1, &n \ge 1
      \end{matrix}\right.
    $$

14. 首先，有$P_0=1$。第$n(n \ge 1)$个平面使得区域增加$k$个，当且仅当它将$k$个区域一分为二。它将$k$个区域一分为二，当且仅当这个平面被分为$k$段区域。由于两个平面最多有一条交线，故$k$最大为$L_{n-1}=1+\frac{n(n-1)}{2}$，有$P_n=P_{n-1}+1+\frac{n(n-1)}{2}=1+n+\frac{n(n+1)(n-1)}{6}$。
     即可得$P_5=26$,而
    $$
    P_n=\left\{\begin{matrix}
      1, &n=0 \\
      P_{n-1}+1+\frac{n(n-1)}{2}, &n > 0
      \end{matrix}\right.
    $$

15. 显然$I(n)$仅对$n \ge 2$有效。可以确定有$I(2)=2,I(3)=1$。与约瑟夫问题类似，对$n>1$有以下结论:
    $$
    \begin{align*}
    I(2n)&=2I(n)-1 \\
    I(2n+1)&=2I(n)+1
    \end{align*}
    $$
    用二进制表示即为:
    $$
    \begin{align*}
    I((10)_2)&=2 \\
    I((11)_2)&=1 \\
    I((1a_1 \cdots a_{n-1})_2)&=2I((1a_1 \cdots a_{n-2})_2)+2a_{n-1}-1 \\
    \end{align*}
    $$
    连续代入得:
    $$
    \begin{align*}
    I((1a_1 \cdots a_{n-1})_2) &= 2^{n-2} \cdot I((1a_1)_2)+\sum_{i=1}^{n-2}{2^{i}a_{n-i}}-\sum_{i=0}^{n-3}{2^{i}} \\
    &=2^{n-2} \cdot 2^{1-a_1}+(a_2 \cdots a_{n-1}0)_2+1-2^{n-2}  \\
    &=2^{n-2} \cdot (2^{1-a_1}-1)+(a_2 \cdots a_{n-1}1)_2 \\
    &= \left\{\begin{matrix}
      (1\underset{n-2个0}{ \underbrace{0 \cdots 0}})_2+(a_2 \cdots a_{n-1}1)_2, &a_1=0 \\
      (a_2 \cdots a_{n-1}1)_2, &a_1=1
      \end{matrix}\right.\\
    &=((\neg a_1 \land a_2)((\neg a_1) \oplus a_2) \cdots a_{n-1}1)_2
    \end{align*}
    $$
    故
    $$
    \begin{align*}
    I(2^m+l) &= 2^{m-1}+2l+1\\
    I(2^m+2^{m-1}+l) &= 2l+1 \\
    其中，0 \le l < 2^{m-1}
    \end{align*}
    $$
    
16. 设$g(n)=A(n)\alpha+B(n)\gamma+C(n)\beta_0+D(n)\beta_1$
     记$\textbf{P}=(\alpha,\gamma,\beta_0,\beta_1),n=(b_0b_1 \cdots b_{m-1})_2$

     代入$\textbf{P}=(1,0,0,0)$，得$g((b_0b_1 \cdots b_{m-1})_2)=A((b_0b_1 \cdots b_{m-1})_2)=(1\underset{m个0}{ \underbrace{0 \cdots 0}})_3$，

     代入$\textbf{P}=(0,0,0,1)$，得:
    $$
    \begin{align*}
    g(n)&=D(n) \\
    g(1)&=0 \\
    g(2n)&=3g(n) \\
    g(2n+1)&=3g(n)+1
    \end{align*}
    $$
    可得$D((b_0b_1 \cdots b_{m-1})_2)=\sum_{i=1}^{m}3^{i-1}b_{m-i}=(b_0b_1 \cdots b_{m-1})_3$
    
    代入$g(n)=n$，得$\textbf{P}=(1,-1,0,1)$，即$A(n)-B(n)+D(n)=n$
    代入$g(n)=1$，得$\textbf{P}=(1,0,-2,-2)$，即$A(n)-2C(n)-2D(n)=1$
    
    可得
    $$
    \begin{align*}
    B((b_0b_1 \cdots b_{m-1})_2)&=(1b_0\cdots b_{m-1})_3-(b_0b_1 \cdots b_{m-1})_2 \\
    C((b_0b_1 \cdots b_{m-1})_2)&=(\underset{m个1}{ \underbrace{1 \cdots 1}})_3-(b_0b_1 \cdots b_{m-1})_3
    \end{align*}
    $$
    整理得:
    $$
    \begin{align*}
    g((b_0b_1 \cdots b_{m-1})_2)=&(1\underset{m个0}{ \underbrace{0 \cdots 0}})_3\alpha\\ 
    &+((1b_0\cdots b_{m-1})_3-(b_0b_1 \cdots b_{m-1})_2)\gamma\\ 
    &+((\underset{m个1}{ \underbrace{1 \cdots 1}})_3-(b_0b_1 \cdots b_{m-1})_3)\beta_0\\
    &+(b_0b_1 \cdots b_{m-1})_3\beta_1
    \end{align*}
    $$

## 考试题

17. 将起点和终点桩记为A和B，剩余的记为C和D，移动$n(n+1)/2,n>0$可以分为以下几步:

    1. 将$n(n-1)/2$个盘子移动到C或D上（不妨设为C），需要$W_{n(n-1)/2}$步。
    2. 将剩下$n$个盘子移动到B上。由于C被占用，故需要$T_n$步。
    3. 将$n(n-1)/2$个盘子移动到B上，需要$W_{n(n-1)/2}$步。

    故有$W_{n(n+1)/2}\le 2W_{n(n-1)/2}+T_n$
    欲使所有$n \ge 0$，存在$W_{n(n+1)/2} \le f(n)$。只需使
    $$
    f(n)=\left\{\begin{matrix}
    0,&n=0 \\
    2f(n-1)+T_n,&n>0
    \end{matrix}\right.
    $$
    连续展开并整理得$f(n)=\sum_{i=0}^{n-1}2^{i}T_{n-i}=(n+1)2^n-1$

    * 尽管与标准答案不同，但仍然满足题意。

18. 对于第$j$条折线，可根据锯齿点分为2股射线。对左股，其倾斜角有$cot\alpha_j=-(n^j+n^{-n})$。对于右股，其倾斜角有$cot\beta_j=-n^{j}$，显然有$cot\alpha_j<cot\beta_j$，或者说，$\alpha_j > \beta_j$。
    要形成$Z_n$个区域，需对每个折线与其余所有折线的两股都有不重合的交点。只需已有$i-1(1<i \le n)$条折线时新增一条折线$i$，使这个折线的两股与前$i-1$个折线的两股都有交点，且不与现有交点重合。
    对于前一点，只需对所有$k<i$，有$cot\beta_i<cot\alpha_k$即$n^{i-k}>n^{-n}$，显然成立。
    对于后一点，由于两折线之内的四个交点必然各不相同。故只需对所有折线组合$(i,k)(i \ne k)$，其交点的纵坐标(四个交点通称为$y_{ik}$)取值范围间互相无公共区间。
    而其中，$y_{ik}$满足$|y_{ik}cot\theta_i|-|y_{ik}cot\theta_k|=n^{2j}-n^{2k}(\theta_j表示\alpha_j和\beta_j其中之一)$，整理得$y_{ik}=\frac{(n^{i}+n^{k})(n^{i}-n^{k})}{n^{i}-n^{k}+\upsilon}(\upsilon=0或\pm n^{-n})$。显然$n^i+n^k-n^{-n}\le y_{ik}\le n^i+n^k+n^{-n},即y_{ik} \in\delta (n^i+n^k,n^{-n})$。对于任意指定合法折线组合$(a,b),(c,d)$，有$(n^a+n^b)-(n^c+n^d)=(n^a-n^c)+(n^b-n^d)>2\ge 2n^{-n}$，故任意$y_{ab},\ y_{cd}$的取值范围互相无公共区间。

    综上，两个条件都满足，能形成$Z_n$个区域。
19. 不可能，说理如下
    <img src="./concreteMathematics.assets/%E5%BE%AE%E4%BF%A1%E5%9B%BE%E7%89%87_20240721005203.jpg" style="zoom:50%;" />
    如图所示，欲作一直线，使直线与折线有两个交点，显然需将直线作在锯齿外。而对于一条射线，其源点必须在阴影内。因此，欲作一折线与该折线相交，则至少需要将锯齿尖作在阴影内
    
    由于锯齿本身有$30^{\circ}$夹角，从阴影发出的射线与原锯齿两射线的夹角必须有$0<\alpha, \alpha+30^{\circ}<150^{\circ}$，即$0<\alpha<120^{\circ}$。两个折线形成的角图形的角平分线之间的角度$\theta=\alpha+30^{\circ},30^{\circ}<\theta<150^{\circ}$。
    <img src="./concreteMathematics.assets/%E5%89%A9%E4%BD%99%E7%A9%BA%E9%97%B4.jpg" style="zoom: 25%;" />
    
    出于类似的原因，欲再作一条满足要求的折线必须将锯齿作于图中阴影区域内。易知相同角度下，锯齿尖越近，剩余阴影越大。当两个锯齿尖足够近时，可以将这两个角等效为一个角，该角的两边由两条折线中最"外侧"的射线组成。新作的折线必要能与此角(折线)有4交点。
    由于$\theta > 30^{\circ} \gg 0$，且$\theta$的取值范围将随锯齿添加而进一步收缩，并且最好情况下满足$30^{\circ}<\theta<180^{\circ}-30^{\circ} \cdot (n-1)$，$n$表示(算上新加入的)锯齿的数量。即最多只能有5个(或更少)个锯齿满足$Z_n$
    
20. 本题与16题的题干、解法极为相似，故不再赘述。

21. 假设剩余$m$人时处决的编号为$K(m,q)$，现要求一$q$使$\{K(2n,q),\cdots ,K(n+1,q)\}=\{n+1, \cdots ,2n\}$。|
    易知
    $$
    \begin{align*}
    K(2n,q)&=q \mod 2n\\
    K(m,q)-1&=(q\mod m+K(m+1,q)-1) \mod (m+1)
    \end{align*}
    $$
    

## 附加题

22. 显然，$1$个凸多边形能形成一个韦恩图。假设$n-1$个凸多边形能形成一个韦恩图，只需在增加一个凸多边形的情况下使这个凸多边形穿过现有$2^{n-1}$个区域即可使$n$个凸多边形能形成一个韦恩图。
23. 能

## 研究题

24. 
