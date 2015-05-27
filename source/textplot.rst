textplot
========

描述
    该函数在一个图形窗口显示文本输出。它等同于“print”，除了输出是作为标绘图显示。

用法
::

    textplot(object, halign="center", valign="center", cex, max.cex = 1, cmar = 2, rmar = 0.5, show.rownames = TRUE,
             show.colnames = TRUE, hadj = 1, vadj=NULL, row.valign = "center",
             heading.valign = "bottom", mar = c(0, 0, 0, 0) + 0.1, col.data = par("col"), col.rownames = par("col"),
             col.colnames = par("col"), wrap = TRUE, wrap.colnames = 10, wrap.rownames = 10, ...)

    replaceTabs(text, width=8)

参数
    :object: 要显示的对象
    :halign: x方向对齐方式，“center”、“left”或“right”之一
    :valign: y方向对齐方式，“center”、“top”或“bottom”之一
    :cex: 字符大小，详见par 。如果没有设置，代码将试图用能够显示整个对象的最大值
    :mar: 图片边缘，参见有关par文档
    :rmar, cmar: 行和列间的空间，以字母M大小的分数计
    :show.rownames, show.colnames: 逻辑值，指示是否显示行或列的名称
    :hadj,vadj: 元素在矩阵单元中垂直和水平位置。这些与adjgraphics 参数有相同的含义（参见par）
    :col.data: 数据元素颜色。如果提供一个值，那么所有数据就用相同的颜色。如果提供了一个与数据维度匹配的矩阵，那么每个数据元素将获得设定的颜色
    :col.rownames, col.colnames: 行名称和列名称各自的颜色。要么设定为一个标量，要么设定为有合适长度的向量
    :max.cex: 设定最大文本大小作为上限
    :row.valign: 设置行的垂直对齐方式为“top”、“bottom”或（缺省）“center”
    :heading.valign:  设置顶部（heading）的垂直对齐方式为“top”、（缺省）“bottom”或 “center”
    :wrap: 如果为TRUE（缺省），将折行列名称和行名称
    :wrap.colnames: 字符数目，之后的列名称将被折行，缺省为10
    :wrap.rownames: 字符数目，之后的行名称将被折行，缺省为10
    :text: replaceTabs 函数中，要处理的字符串
    :width: replaceTabs 函数中，用来替换tab的空格数
    :...: 传递给text plotting命令或特定对象方法的可选参数

说明
    新建一个标绘图，对象用适合绘图区域的大号字体显示。halign 和valign 参数可被用来控制绘图区内字符串的位置。

    对矩阵和向量，有一个特别的textplot函数可用，它按照列元素大小设置的列宽单独绘出每个单元。如果呈现出来，行和列标签将以粗体字显示。

    textplot也使用replaceTabs，一个将tab替换成合适数量空格的字符串的函数。该函数也由Gregory R. Warnes编写，包括在gplots包中。

另见
    plot text capture.output textplot

范例
::

    # Also see the examples in the original gplots textplot function
    data(managers)
    textplot(table.AnnualizedReturns(managers[,1:6]))

    # This was really nice before Hmisc messed up 'format' from R-base
    # prettify with format.df in hmisc package
    # require("Hmisc")
      result = t(table.CalendarReturns(managers[,1:8]))[-1:-12,]

    # textplot(Hmisc::format.df(result, na.blank=TRUE, numeric.dollar=FALSE, cdec=rep(1,dim(result)[2])),
    #          rmar = 0.8, cmar = 1,  max.cex=.9, halign = "center", valign = "top", row.valign="center",
    #          wrap.rownames=20, wrap.colnames=10, col.rownames=c("red", rep("darkgray",5), rep("orange",2)),
    #          mar = c(0,0,4,0)+0.1)

    # title(main="Calendar Returns")


