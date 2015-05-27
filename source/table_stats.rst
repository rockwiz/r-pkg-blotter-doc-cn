table.Stats
===========

描述
    收益概要：统计量和样式化事实。返回一组匹配传入数据期间的基本统计量（例如，月度收益将获得月度统计量，每日收益对应每日统计，等等）。

用法
::

    table.Stats(R, ci = 0.95, digits = 4)

参数
    :R: 一个资产收益的向量、矩阵、数据框、时间序列或zoo, xts对象
    :ci: 置信区间，缺省为95%
    :digits: 进行四舍五入的指定位数

说明
    同时显示用来在一组证券或基金间进行比较的一组相关统计量。解释结果时，小心在意缺损数据或不相等的时间序列。

范例
::

    data(edhec)
    table.Stats(edhec[,1:3])
    t(table.Stats(edhec))

    result=t(table.Stats(edhec))
    require("Hmisc")
    textplot(format.df(result, na.blank=TRUE, numeric.dollar=FALSE, cdec=c(rep(1,2),rep(3,14))),
             rmar = 0.8, cmar = 1.5,  max.cex=.9, halign = "center", valign = "top", row.valign="center",
             wrap.rownames=10, wrap.colnames=10, mar = c(0,0,3,0)+0.1)
    title(main="Statistics for EDHEC Indexes")


