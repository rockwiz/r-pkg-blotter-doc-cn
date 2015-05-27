VaR
===

描述
    利用各种分析方法为单变量、成分和边际情况计算在险价值。

用法
::

    VaR(R = NULL, p = 0.95,..., method = c("modified",  "gaussian", "historical", kernel"),
        clean = c("none", "boudt", "geltner"), portfolio_method = c("single", "component","marginal"),
        weights = NULL, mu = NULL, sigma = NULL, m3 = NULL, m4 = NULL, invert = TRUE)

参数
    :R: 一个资产收益的向量、矩阵、数据框、时间序列或zoo, xts对象
    :p: 用于计算的置信水平，缺省p=.95
    :method: “modified”、“Gaussian”、“historical”、“kernel”之一，参见说明部分
    :clean: 经由Return.clean的数据清洗方法。目前选项为“none”、“boudt”或“geltner”
    :portfolio_method: “single”、“component”、“marginal”之一，定义是做单变量、成分还是边际计算，参见说明部分
    :weights: 组合权重向量，缺省为NULL，参见说明部分
    :mu: 如果为单变量，mu是序列均值。否则，mu是收益序列均值向量，缺省为NULL，参见说明部分
    :sigma: 如果为单变量，sigma 是序列方差。否则，sigma是收益序列协方差矩阵，缺省为NULL，参见说明部分
    :m3: 如果为单变量，m3是序列偏度。否则，m3是收益序列协偏度矩阵，缺省为NULL，参见说明部分
    :m4: 如果为单变量，m4是序列过量峰度。否则，m4是收益序列协峰度矩阵，缺省为NULL，参见说明部分
    :invert: TRUE/FALSE，是否反转VaR度量。参见说明部分
    :...: 其它要传入的参数

说明
    **背景**

    该函数提供几个估计收益序列的在险价值（Value at Risk ，VaR）或投资组合的成分VaR的方法。注意VaR大小写的惯常使用方式，
    不要与var（variance，方差）和VAR（vector auto-regression，向量自回归）混淆。VaR是度量下方风险的工业标准。对收益序列，
    VaR定义为收益负值的高分位数（例如，~a 95%或 99%分位数）。该分位数需要估计。对足够大的数据集，也许选择使用分位数计算出的经验分位数。
    如果作出了收益分布的（正确）假设，如正态分布，可以获得更高效的VaR估计。如果收益序列是有偏度的，并且/或者有过量峰度，
    VaR的Cornish-Fisher估计可能更合适。对投资组合的VaR，将总的组合VaR分解为每个组合成分的风险贡献，也很有趣；对上述VaR估计量，
    这样的分解在金融意义上是可能的。

    **单变量VaR估计方法**

    在一个概率水平p（如95%）上的VaR是负收益的p分位数，或等同地，是收益c=1-p分位数的负值。在一组存在足够长历史的收益中，
    每期（per-period）VaR仅仅是期间负收益的分位数 :math:`VaR=q.99`

    其中，q.99是负收益序列的99%经验分位数。该方法有时也称为“历史VaR”（historical VaR），因为它是根据收益分布的事后（ex post）分析，
    并可通过设置method="historical"来存取。

    当没有用于非参或历史VaR的足够长的收益，或者希望建立一个更接近理想分布的模型，通常用基于分布的参数估计。J.P. Morgan的风险矩阵参数
    均值VaR（RiskMetrics parametric mean-VaR）发表于1994年，这种估计参数均值VaR的方法已经成为大多数文献公认的“VaR”方法，
    也是我们所实现的VaR方法。参见Return to RiskMetrics: Evolution of a Standard
    （http://www.riskmetrics.com/publications/techdocs/r2rovv.html）。

    通过更精确地估计风险分位数分布的尾部形状，参数均值VaR在刻画分布尾部方面做得更好。最常用的估计是收益序列的正态（或高斯）分布。
    这种情况下，VaR估计需要均值收益，收益分布和分布方差σ。最常见情况下，参数VaR计算如下：

    .. math::

        \sigma=variance(R)\\
        VaR=-\overline{R}-\sqrt{\sigma}\centerdot{\mathit{z}_c}

    其中 :math:`\mathit{z}_c` 是标准正态分布的c-分位数。在R中以qnorm(c)表示，并可通过设置method="gaussian"存取。

    其它形式的参数均值VaR估计采用不同的损失分布以更好地说明可能的下方风险的肥尾现象。VaR包，现在已经孤立了，包含模拟和估计对数正态的
    方法VaR.norm和广义帕累托分布VaR.gpd来解决参数或非参均值VaR计算在有限大小样本或可能的肥尾分布中的问题。也有一个VaR.backtest函
    数运用模拟方法来创建损失可能分布的更稳健估计。也可用多风险因子的协方差矩阵，但并不常见。我们试图在PerformanceAnalytics将来的发
    行版本中将那些孤立功能合并进来。

    均值VaR的局限在许多文献中都有提及。传统均值VaR的局限都与对称分布的使用有关。模拟、重采用或帕累托分布有助于进行更精确的预测，
    但它们对于显著非正态（偏度或峰度）分布的资产还是有瑕疵。Zangari (1996) and Favre and Galeano(2002)利用Cornish-Fisher
    扩展考虑进非正态分布（偏度和峰度）的高阶矩，提供一种改进VaR（modified VaR）计算，而如果收益流服从标准分布，则退化为标准（传统的）
    均值VaR。这种度量现在在文献中被广泛引用和使用，通常用来指“改进VaR”（Modified VaR）或“
    改进Cornish-Fisher VaR”（Modified Cornish-Fisher VaR）。它们的计算公式为

    .. math::

        \mathit{z}_{cf}=\mathit{z}_c+\frac{({{\mathit{z}}_c}^2-1)S}{6}+\frac{({{\mathit{z}}_c}^2-3{\mathit{z}_c})K}{24}+\frac{({{2\mathit{z}}_c}^3-5{\mathit{z}_c}){\mathit{s}^2}}{36}\\

        cornish-FisherVar=-\overline{R}-\sqrt{R}\centerdot\mathit{z}_{cf}

    其中S是R的偏度，K是R的过量峰度。

    当收益为正态分布时，Cornish-Fisher VaR 退化成传统的均值VaR。有鉴于此，VaR是一个封装函数。
    Cornish-Fisher扩展也自然包括许多重采样或蒙特卡洛（Monte-Carlo）模拟等高强度计算技术所揭示的收益变动性。这是VaR函数的缺省方法，
    可通过设置method="modified"存取。

    Favre and Galeano也为他们组合优化/分析工作在改进夏普比率中采用改进VaR作为收益/风险度量，有关详情，参见SharpeRatio.modified。

    **成分VaR（Component VaR）**

    通过设置portfolio_method="component" ，可以计算投资组合中每个元素的风险贡献。这种情况下，函数的返回值将是一个带三个分量的列表：
    单变量组合VaR，每个成分相对组合VaR的标量贡献（它们的总和为组合VaR），百分比风险贡献（它们总和为100%）。

    对VaR的数值型和百分比贡献都可以为正和为负。对成分VaR的负贡献表明是一个组合的风险分散者。提高该头寸的权重将减少总的组合VaR。

    如果没有通过weights传递一个加权向量，函数将假设一个等权重（中性）投资组合。

    文献中提出多个风险分解方式。一个“质朴”（na?ve）方式是将风险贡献设为等同于它们的孤立（stand-alone）风险。这种方式过度简单，
    忽略了对相关风险因子有不同影响的单元的重要分散效应。一个替代方式是用头寸在组合中的权重乘以组合VaR关于成分权重的偏导数来度量VaR贡献。

    .. math::

        C_i{VAR}=\mathit{w}_i\frac{\partial{VaR}}{\partial\mathit{w}_i}

    由于组合VaR与组合的规模成线性关系，根据Euler 定理，组合VaR是这些风险贡献之和。Gourieroux (2000)显示了对VaR，
    组合风险的数学分解具有金融含义。当投资组合的收益等于负的组合VaR时，它等于资产相对组合收益期望贡献的负值。

    .. math::

        C_i{VAR}=-E[\mathit{w}_i\mathit{r}_i|\mathit{r}_p=-VaR]

    对高斯VaR的分解，需要估计的均值和协方差矩阵。对改进VaR的分解，也需要估计协偏度和协峰度矩阵。如果r为Nx1维收益向量，μ 为均值向量，
    那么 :math:`N\times{N}^2` 协偏度矩阵是：

    .. math::

        m3=E[(r-\mu){(r-\mu)}^{'}\otimes{(r-\mu)}^{'}]

    :math:`N\times{N}^3` 协峰度矩阵是

    .. math::

        m4=E[(r-\mu){(r-\mu)}^{'}\otimes{(r-\mu)}^{'}\otimes{(r-\mu)}^{'}]

    其中 :math:`\otimes` 代表Kronecker积。该矩阵可通过函数skewness.MM 和kurtosis.MM 估计。
    Martellini and Ziemann (2007)提出了更高效的估计量（estimators），会在将来实现。

    如Cont、Deguest和Scandolo (2007)讨论过的，VaR度量估计对单个异常值稳健相当重要。尤其在改进VaR和它的成分分解情况下，
    因为它们使用高阶矩。缺省地，组合矩根据它们的样本对应部分估计。如果clean="boudt"，那么当1-p最极端观测值被检测为异常值，
    它们会被温莎化（winsorized9）。有关详情，参见Boudt、 Peterson和Croux (2008) 和Return.clean。如果你的数据由高非流动性资产组成，
    那么clean="geltner"也许在缩减自相关带来的扭曲方面更合适，参见Return.Geltner。

    Epperlein and Smillie (2006)为成分风险贡献引入了一种非参核估计量，通过设置method="kernel" 和portfolio_method="component"可得。

    **边际VaR（Marginal VaR）**

    不同论文对此称呼不一样。此处提到的Denton and Jayaraman论文中，该计算称为递增VaR（Incremental VaR）。我们选择更加通用的做法，
    把组合包含某证券与不包含此证券在VaR上的差异称为“边际差异”（difference at the Margin），因而命名为边际VaR（Marginal VaR）。
    这确是不可思议地令人困惑，但此时在文献中尚未得到解决。Simon Keel and David Ardia (2009)在他们题为“Generalized Marginal Risk”的
    论文中试图协调一些定义问题使其一致并解决这种度量的一些缺点。希望他们改进的边际风险度量在将来能包括进来。

    在既有组合和权重的情况下，我们觉得边际VaR不是很有用，倾向于使用成分VaR。在组合经理尝试评估可能包括在一个组合中的两个或多个类似证券时，
    或者考虑将一种证券替换成另一种类似证券时，边际VaR有指导意义。这种情况下，它展示了考虑中的每种证券对组合的特定分散效应和替代效应。
    通过指明哪种证券对组合风险影响较小，以及总体组合风险与可能组合风险间的差异能给资产经理提供补充信息。

备注
    VaR度量的invert（反转）选项将调和理论和实践工作者。VaR作为分位数的负值的数学定义常常会产生一个正数。实践工作者争辩说，VaR意味损失，
    应该内在的与分位数（一个负数）保持一致。对图表而言，不同偏好选项也许应用于清晰和紧凑。有鉴于此，我们提供该选项，
    并将缺省值设为TRUE以让收益与PerformanceAnalytics 之前版本保持一致。哪种方式更好，我们不做判断。

    The prototype of the univariate Cornish Fisher VaR function was completed by Prof. Diethelm Wuertz.
    All corrections to the calculation and error handling are the fault of Brian Peterson.

参考

* Boudt, Kris, Peterson, Brian, and Christophe Croux. 2008. Estimation and decomposition of downside risk for portfolios with non-normal returns. 2008. The Journal of Risk, vol. 11, 79-103.
* Cont, Rama, Deguest, Romain and Giacomo Scandolo. Robustness and sensitivity analysis of risk measurement procedures. Financial Engineering Report No. 2007-06, Columbia University Center for Financial Engineering.
* Denton M. and Jayaraman, J.D. Incremental, Marginal, and Component VaR. Sunguard. 2004.
* Epperlein, E., Smillie, A. Cracking VaR with kernels. RISK, 2006, vol. 19, 70-74.
* Gourieroux, Christian, Laurent, Jean-Paul and Olivier Scaillet. Sensitivity analysis of value at risk. Journal of Empirical Finance, 2000, Vol. 7, 225-245.
* Keel, Simon and Ardia, David. Generalized marginal risk. Aeris CAPITAL discussion paper.
* Laurent Favre and Jose-Antonio Galeano. Mean-Modified Value-at-Risk Optimization with Hedge Funds. Journal of Alternative Investment, Fall 2002, v 5.
* Martellini, Lionel, and Volker Ziemann. Improved Forecasts of Higher-Order Comoments and Implications for Portfolio Selection. 2007. EDHEC Risk and Asset Management Research Centre working paper.
* Return to RiskMetrics: Evolution of a Standard http://www.riskmetrics.com/publications/techdocs/r2rovv.html
* Zangari, Peter. A VaR Methodology for Portfolios that include Options. 1996. RiskMetrics Monitor, First Quarter, 4-12.
* Rockafellar, Terry and Uryasev, Stanislav. Optimization of Conditional VaR. The Journal of Risk, 2000, vol. 2, 21-41.

另见
    SharpeRatio.modified chart.VaRSensitivity Return.clean

范例
::

    data(edhec)
    # first do normal VaR calc
    VaR(edhec, p=.95, method="historical")
    # now use Gaussian
    VaR(edhec, p=.95, method="gaussian")
    # now use modified Cornish Fisher calc to take non-normal distribution into account
    VaR(edhec, p=.95, method="modified")
    # now use p=.99
    VaR(edhec, p=.99)
    # or the equivalent alpha=.01
    VaR(edhec, p=.01)
    # now with outliers squished
    VaR(edhec, clean="boudt")
    # add Component VaR for the equal weighted portfolio
    VaR(edhec, clean="boudt", portfolio_method="component")

