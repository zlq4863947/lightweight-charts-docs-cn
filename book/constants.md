# 常量

`lightweight-charts`包导出一些枚举，您可以使用这些枚举来设置图表，系列等。

这些枚举在这里描述。

## LineType

`LineType` 枚举用于指定系列的行类型，例如面积或线。
它具有以下值：

- `LineType.Simple`
- `LineType.WithSteps`

## LineStyle

`LineStyle` 枚举用于指定区域和线系列，十字线和网格线，价格线和基线的线的样式。
它具有以下值：

- `LineStyle.Solid`
- `LineStyle.Dotted`
- `LineStyle.Dashed`
- `LineStyle.LargeDashed`
- `LineStyle.SparseDotted`

## PriceScaleMode

`PriceScaleMode` 枚举用于指定价格刻度模式。

它具有以下值：

- `PriceScaleMode.Normal` - 普通模式.

  Price scale shows prices and price range is changing linearly.
  价格刻度显示价格和价格范围线性变化。

- `PriceScaleMode.Logarithmic` - 对数模式.

  Price scale shows prices, but price range is changing logarithmically.
  价格刻度显示价格，但价格范围以对数方式变化。

- `PriceScaleMode.Percentage` - 百分比模式.

  价格刻度显示价格的百分比值。在此模式下，第一个可见值为`0％`。

- `PriceScaleMode.IndexedTo100`- 索引为 100 模式

  与百分比模式相同，但第一个值变为 100

## CrosshairMode

`CrosshairMode` 枚举用于指定十字准线模式。

它具有以下值：

- `CrosshairMode.Magnet` - 十字准线的磁铁模式。

十字线水平线锚定到收盘价。

- `CrosshairMode.Normal` - 十字准线的正常模式。

十字线在图表上自由移动。
