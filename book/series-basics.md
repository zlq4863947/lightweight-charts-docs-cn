# 系列基础

每个系列都有一组共同的属性和方法，无论其类型如何。

例如，要创建任何类型的系列，您可以传递`title`参数来设置系列标题。

这里描述了这些**常见**参数和 API。如果您想查看特定类型系列的 API，请参阅相关文档页面。

## 创建系列

要创建任何类型的系列，您需要调用`chart.add <type> Series`方法，其中`<type>`是要添加到图表的系列类型。

例如:

- 创建线系列:

  ```javascript
  const lineSeries = chart.addLineSeries();
  ```

- 创建面积系列:

  ```javascript
  const areaSeries = chart.addAreaSeries();
  ```

- 创建 K 线系列:

  ```javascript
  const barSeries = chart.addBarSeries();
  ```

## 参数

创建系列时，您可以指定要更改的系列参数。

以下是全部系列的通用参数：

| 名称           | 类型              | 默认值      | 描述                                                                        |
| -------------- | ----------------- | ----------- | --------------------------------------------------------------------------- |
| `overlay`      | `boolean`         | `false`     | 系列是否为 overlay                                                          |
| `title`        | `string`          | `''`        | 将图表添加到图表时，可以命名系列。 此名称将显示在最后一个值标签旁边的标签上 |
| `scaleMargins` | `{ top, bottom }` | `undefined` | *overlay*的[边距](#scale-margins)                                           |

例子:

```javascript
const lineSeries = chart.addLineSeries({
  overlay: true,
  title: "Series title example",
  scaleMargins: {
    top: 0.1,
    bottom: 0.3
  }
});
```

### Overlay

将任何系列添加到图表时，您可以指定是否要将目标系列附加到价格轴。默认情况下，系列附加到价格轴。
这意味着可以使用价格轴来缩放系列。请注意，价格轴可见范围取决于系列值。
相比之下，叠加系列只是在独立于价格轴的图表上绘制。

```javascript
const lineSeries = chart.addLineSeries({
  overlay: true
});
```

### 标题

将任何系列添加到图表时，可以通过向`title`属性添加字符串来命名。
此名称将显示在最后一个值标签旁边的标签上。

```javascript
const lineSeries = chart.addLineSeries({
  title: "Series title example"
});
```

### 刻度边距

通常，我们不希望系列绘制的图表边框太靠近。它需要在顶部和底部有一些边距。

默认情况下，库在数据下方（10％）和数据上方（20％）保留空白区域。

可以使用图表选项为可见轴调整这些值。但是，您也可以通过 Overlay 系列定义它们。

边距是具有以下属性的对象：

- `top`
- `bottom`

对象的每个值都是 0（0％）和 1（100％）之间的数字。

```javascript
const lineSeries = chart.addLineSeries({
  overlay: true,
  scaleMargins: {
    top: 0.6,
    bottom: 0.05
  }
});
```

上面的代码将系列放在图表的底部。

您可以使用`ChartApi.applyOptions`为可见轴更改边距：

```javascript
chart.applyOptions({
  priceScale: {
    scaleMargins: {
      top: 0.6,
      bottom: 0.05
    }
  }
});
```

## 数据

每个系列都有自己的数据类型。 请参阅系列页面以确定该系列使用的数据类型。

## 方法

### options

返回当前应用的完整选项集，包括默认值。

### applyOptions

此方法用于将新选项应用于系列。

您可以在创建系列时初始选项设置，或使用系列的 `applyOptions` 方法更改现有选项。

请注意，您只能传递要更改的选项。

每个系列类型都有自己的选项。但是，所有类型的系列都有一些共同的选项。

#### Price line

价格线是在最后价格水平上绘制的水平线。

默认情况下，其颜色由最后一个 k 线颜色（或线条和面积图上的线条颜色）决定。

您可以设置它的宽度，样式和颜色，或使用以下选项将其禁用：

| 名称               | 类型                                  | 默认值             | 描述                                      |
| ------------------ | ------------------------------------- | ------------------ | ----------------------------------------- |
| `priceLineVisible` | `boolean`                             | `true`             | 如果为 true，则会在图表上显示系列的价格线 |
| `priceLineWidth`   | `number`                              | `1`                | 价格线的宽度（以像素为单位）              |
| `priceLineColor`   | `string`                              | `''`               | 价格线的颜色                              |
| `priceLineStyle`   | [LineStyle](./constants.md#linestyle) | `LineStyle.Dotted` | 价格线的样式                              |

例子:

```javascript
series.applyOptions({
  priceLineVisible: false,
  priceLineWidth: 2,
  priceLineColor: "#4682B4",
  priceLineStyle: 3
});
```

#### Price labels

默认情况下，最后一个价格值作为显示在价格刻度的相关级别的标签。
还有一个隐藏它的选项。

| 名称               | 格式      | 默认值 | 描述                                                |
| ------------------ | --------- | ------ | --------------------------------------------------- |
| `lastValueVisible` | `boolean` | `true` | 如果为 true，则在价格标尺上显示具有当前价格值的标签 |

Example:

```javascript
series.applyOptions({
  lastValueVisible: false
});
```

#### Base line

基准线是在`percentage`和`indexedTo100`模式下在零级绘制的水平线。
您可以设置此行的宽度，样式和颜色，或使用以下选项将其禁用：

| Name              | Type                                  | Default           | Description                             |
| ----------------- | ------------------------------------- | ----------------- | --------------------------------------- |
| `baseLineVisible` | `boolean`                             | `true`            | 如果为 true，则在图表上显示系列的基准线 |
| `baseLineWidth`   | `number`                              | `1`               | 基准线的宽度（以像素为单位）            |
| `baseLineColor`   | `string`                              | `'#B2B5BE'`       | 基准线的颜色                            |
| `baseLineStyle`   | [LineStyle](./constants.md#linestyle) | `LineStyle.Solid` | 基准线的样式                            |

例子:

```javascript
series.applyOptions({
  baseLineVisible: true,
  baseLineColor: "#ff0000",
  baseLineWidth: 3,
  baseLineStyle: 1
});
```

#### Price format

提供四种价格格式，用于在价格标尺上显示:

- `price` 格式，默认设置，显示绝对价格值
- `volume` 格式，减少超过 1000 的值的位数，用字母替换零。 例如，**1000**绝对价格值以格式化显示为**1K**。
- `percent` 格式，用百分比变化替换绝对值。
- `custom` 格式，使用用户定义的函数进行价格格式化，可以在某些特定情况下使用，标准格式器不包括这些函数

以下选项可用于设置任何类型的系列显示的价格格式:

| 名称        | 类型                                                     | 默认值      | 描述                                   |
| ----------- | -------------------------------------------------------- | ----------- | -------------------------------------- |
| `type`      | `price` &#124; `volume` &#124; `percent` &#124; `custom` | `price`     | 设置按系列显示的价格类型               |
| `precision` | `number`                                                 | `2`         | 指定用于显示价格值的小数位数           |
| `minMove`   | `number`                                                 | `0.01`      | 设置价格值移动的最小步长               |
| `formatter` | `function` &#124; `undefined`                            | `undefined` | 设置`type`为`custom`时使用的格式化函数 |

例子:

```javascript
series.applyOptions({
  priceFormat: {
    type: "volume",
    precision: 3,
    minMove: 0.05
  }
});
```

```javascript
series.applyOptions({
  priceFormat: {
    type: "custom",
    minMove: 0.02,
    formatter: function(price) {
      return "$" + price.toFixed(2);
    }
  }
});
```

### setData

允许使用新数据设置/替换所有现有数据。

参数类型为系列项目数组。

例子:

```javascript
lineSeries.setData([
  { time: "2018-12-12", value: 24.11 },
  { time: "2018-12-13", value: 31.74 }
]);
```

```javascript
barSeries.setData([
  {
    time: "2018-12-19",
    open: 141.77,
    high: 170.39,
    low: 120.25,
    close: 145.72
  },
  { time: "2018-12-20", open: 145.72, high: 147.99, low: 100.11, close: 108.19 }
]);
```

### updateData

将新数据项添加到现有数据集（如果已通过/最新项的时间相等，则更新最新项）

参数类型为系列项目。

例子:

```javascript
lineSeries.updateData({
  time: "2018-12-12",
  value: 24.11
});
```

```javascript
barSeries.updateData({
  time: "2018-12-19",
  open: 141.77,
  high: 170.39,
  low: 120.25,
  close: 145.72
});
```

## 下一个阅读

- [面积图系列](./area-series.md)
- [美国线图系列](./bar-series.md)
- [Candlestick series](./candlestick-series.md)
- [Histogram series](./histogram-series.md)
- [Line series](./line-series.md)
- [Customization](./customization.md)
