initPortf
=========

描述
    初始化一个组合对象

用法
::

    initPortf(name="default", symbols, initPosQty=0, initDate="1950-01-01", currency="USD", ...)

参数
    :name: 由此产生的组合对象的名称
    :symbols: 组合中证券的标识符列表
    :initPosQty: 初始头寸数量，缺省是0
    :initDate: 给定的第一个收盘价之前的日期，用于包含初始账户证券和初始头寸
    :currency: ISO 货币标识符，用于本地化组合货币
    :...: 任何其它要传递的参数

说明
    构造和初始化一个组合对象，它用于包含交易事务、头寸和归集层次上的数值。

    初始化一个组合对象，由以下构成：

    | $symbols：用于组合中的每一种证券的标识符。用Use names(Portfolio$symbols) 获取证券列表。
    | $symbols$[symbol]$txn：交易事务数据的不规则xts对象。
    | $symbols$[symbol]$posPL：根据交易事务计算而来的头寸损益的规则xts对象。
    | $symbols$[symbol]$posPL.ccy：头寸损益转换为组合货币的规则xts对象。
    | $summary：归集后的组合数值。

    每个证券有三张关联的表。第一张，txn，是交易事务表，一个通过以下列包含交易和其它头寸调整信息不规则时间序列：

    | Txn.Qty：数量，通常以合约数、换手数为单位。正数值表示“买入”，负数值表示“卖出”。
    | Txn.Price：交易达成的价格。
    | Txn.Fees：与交易关联的费用总和。
    | Txn.Value：交易的名义数值。
    | Avg.Txn.Cost：每个买入（卖出）合约支付（收到）的平均净价格经计算后的值。
    | Pos.Qty：合约形成的头寸数量，计算为当前交易和之前头寸的总和。
    | Pos.Avg.Cost：由此产生的头寸经计算后的平均成本。
    | Realized.PL：从出清前一个头寸交易中实现的利润或损失

    第二张表，posPL，是一个用于存储一支证券从交易事务和收盘价中计算得到的损益值。然而，数据是规则时间序列。表的列包括：

    | Pos.Qty：持有的证券头寸数量
    | Pos.Value：头寸的名义价值
    | Txn.Value：发生的交易的净价值
    | Txn.Fees：与交易关联的费用总和
    | Realized.PL：通过交易实现的任何利润或损失
    | Unrealized.PL：与持有头寸关联的任何利润或损失
    | Trading.PL：已实现和未实现的净利润或净损失的总和

    第三张表，posPL.ccy，与第二张表一样，但转换为以组合货币计量。

    对每个组合，概要槽口（the summary slot）包含一张跟踪计算得出的不同时期投资组合信息表。该表包含以下列，其为普通xts时间序列：

    | Long.Value：组合中所持多头头寸名义值之和
    | Short.Value：组合中持有的空头仓位名义价值的总和。
    | Net.Value：组合中名义多头和名义空头价值的总和
    | Gross.Value：组合中名义多头价值和名义空头价值绝对值的总和
    | Txn.Fees：组合在此期间支付的经纪佣金、汇率和代理费用
    | Realized.PL：组合中相关头寸累积的已实现净利润或净损失总和。已实现毛利（Gross realized prots）可通过加入那个时期的Txn.Fees 、经纪佣金费用等计算。
    | Unrealized.PL：期末组合中开放头寸未实现的利润或损失的增减总和。
    | Net.Trading.PL：组合中所有头寸已实现净利润或净损失加上利息收入加上未实现利润或损失的变化
