UpsidePotentialRatio
====================

描述
    计算上方绩效相对下方风险的上方潜势比率。Sortino提出一项夏普比率的改进，只使用下方（downside）方差作为风险度量来更好地证明技能和超额绩效。
    该度量是SortinoRatio。函数UpsidePotentialRatio是进一步的改进，比率方程的分子只有上方（upside），分母只有下方。

用法
::

    UpsidePotentialRatio(R, MAR = 0, method=c("subset","full"))
    UPR(R, MAR = 0, method=c("subset","full"))

参数
    :R: 一个资产收益的向量、矩阵、数据框、时间序列或zoo, xts对象
    :MAR: 最小可接受收益，与收益的周期性相同
    :method: “full”或“subset”之一，指明要使用全序列的长度或MAR 之上（之下）序列子集的长度作为分母，缺省为“subset”

说明
    Sortino 主张风险应该根据没有达到投资目标来度量。这产生了“最小可接受收益”（Minimum Acceptable Return，MAR）的概念。
    所有Sortino提出的度量，包括MAR，对下方风险或极端风险的度量都比使用波动性（收益的标准差）更敏感。

    谨慎选择MAR非常重要，尤其在比较完全不同的投资选择时。如果MAR过低，它不会恰当地捕捉到使投资者忧虑的风险；而如果MAR过高，
    它会不适宜地描绘那些安全可靠的投资。当比较多项投资时，一些论文建议使用无风险收益率作为MAR。实践工作者也许希望为一致性选择一个MAR，
    为一系列方案选择几个标准化的MAR，为投资者客户化定制的一个MAR。

    .. math::

        UPR=\frac{\sum^n_{t=1}(R_t-MAR)}{\delta_{MAR}}

    其中 :math:`\delta_{MAR}` 是DownsideDeviation.

    缺省地，UpsidePotentialRatio中的分子仅使用超过MAR的收益，而（DownsideDeviation中的）分母只使用达不到MAR的收益。Sortino
    认为这是一个潜在收益更精确、更平衡的刻画。SortinoRatio会在周期顶峰时给予经理最多奖励，而对他们过去的平庸表现却没有适当的惩罚。
    其它已经用过全序列，这个通过method参数作为选项提供。

参考
    1. Sortino, F. and Price, L. Performance Measurement in a Downside Risk Framework. Journal of Investing. Fall 1994, 59-65.
    2. Plantinga, A., van der Meer, R. and Sortino, F. The Impact of Downside Risk on Risk-Adjusted Performance of Mutual Funds in the Euronext Markets. July 19, 2001. Available at SSRN: http://ssrn.com/abstract=277352

另见
    SharpeRatio SortinoRatio DownsideDeviation SemiVariance SemiDeviation InformationRatio

范例
::

    data(edhec)
    UpsidePotentialRatio(edhec[, 6], MAR=.05/12) #5 percent/yr MAR
    UpsidePotentialRatio(edhec[, 1:6], MAR=0)

