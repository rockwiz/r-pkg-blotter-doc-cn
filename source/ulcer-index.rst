UlcerIndex
==========
描述
    Peter G. Martin于1987年开发出来，命名为组合经理或投资者引起的担忧。和回撤偏差类似，除了
    将回撤时期和每个低于上一个峰值或高水位线时期的负收益结合起来。长而深的回撤有重大影响，
    因为自从上个峰值后的弱势（underperformance）被平方了。

用法
::

    UlcerIndex(R, ...)

参数
    :R: 一个资产收益的向量、矩阵、数据框、时间序列或zoo, xts对象
    :...: 其它要传入的参数

说明
    .. math::

        UI = \sqrt{\sum_{i=1,2,...,n}\frac{{D^{'}_i}^2}{n}}

    其中， :math:`D^{'}_i` 等于时期i自从上个峰值后的回撤

    该方法对有关时期的频数敏感，并惩罚花费时间追回前个高点的经理。

参考
    Martin, P. and McCann, B. (1989) The investor’s Guide to Fidelity Funds: Winning Strategies for Mutual Fund Investors.
    John Wiley & Sons, Inc. Peter Martin’s web page on UI: http://www.tangotools.com/ui/ui.htm

    ## Test against spreadsheet at: http://www.tangotools.com/ui/UlcerIndex.xls
