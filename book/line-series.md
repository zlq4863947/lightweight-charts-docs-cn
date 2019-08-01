# 折线图系列

折线图是一种图表，它将系列数据点连接成直线。

线系列有一个十字准线标记 - 一个圆形标记，当光标沿着时间刻度移动时，它沿着系列线移动。

![折线图例子](/images/line-series.png "折线图例子")

## 如何创建折线图系列

```javascript
const lineSeries = chart.addLineSeries();

// set data
lineSeries.setData([
  { time: "2018-12-01", value: 32.51 },
  { time: "2018-12-02", value: 31.11 },
  { time: "2018-12-03", value: 27.02 },
  { time: "2018-12-04", value: 27.32 },
  { time: "2018-12-05", value: 25.17 },
  { time: "2018-12-06", value: 28.89 },
  { time: "2018-12-07", value: 25.46 },
  { time: "2018-12-08", value: 23.92 },
  { time: "2018-12-09", value: 22.68 },
  { time: "2018-12-10", value: 22.67 },
  { time: "2018-12-11", value: 27.57 },
  { time: "2018-12-12", value: 24.11 },
  { time: "2018-12-13", value: 30.74 }
]);
```

## 数据格式

可以使用以下选项自定义折线图系列:

- `time` ([时间](./time.md)) - 时间
- `value` (`number`) - 值

## 定制

线条本身可以通过设置颜色，宽度和样式来定制。

此外，默认情况下启用的十字准线标记可以被禁用或调整其半径。

可以使用以下选项自定义:

| 名称                     | 类型                                  | 默认值            | 描述                                 |
| ------------------------ | ------------------------------------- | ----------------- | ------------------------------------ |
| `color`                  | `string`                              | `#2196f3`         | 线条颜色                             |
| `lineStyle`              | [LineStyle](./constants.md#linestyle) | `LineStyle.Solid` | 线条样式                             |
| `lineWidth`              | `number`                              | `3`               | 线宽（以像素为单位）                 |
| `crosshairMarkerVisible` | `boolean`                             | `true`            | 如果为`true`，则十字标记显示在图表上 |
| `crosshairMarkerRadius`  | `number`                              | `4`               | 十字线标记半径（以像素为单位）       |
| `lineType`               | [LineType](./constants.md#linetype)   | `LineType.Simple` | 线条类型                             |

### 例子

- 设置线系列的初始选项:

  ```javascript
  const lineSeries = chart.addLineSeries({
    color: "#f48fb1",
    lineStyle: 0,
    lineWidth: 1,
    crosshairMarkerVisible: true,
    crosshairMarkerRadius: 6,
    lineType: 1
  });
  ```

- 创建系列后更改选项:

  ```javascript
  // 例如，让我们仅覆盖线宽和颜色
  lineSeries.applyOptions({
    color: "rgba(255, 44, 128, 1)",
    lineWidth: 3
  });
  ```

## 下一步是什么

- [定制](./customization.md)
- [常量](./constants.md)
- [时间](./time.md)
