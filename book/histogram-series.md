# 直方图系列

直方图系列是值分布的图形表示。

直方图创建间隔（列）并计算每列中有多少值。

![直方图例子](/images/histogram-series.png "直方图例子")

## 如何创建直方图系列

```javascript
const histogramSeries = chart.addHistogramSeries({
  base: 0
});

// 设置数据
histogramSeries.setData([
  { time: "2018-12-20", value: 20.31, color: "#ff00ff" },
  { time: "2018-12-21", value: 30.27, color: "#ff00ff" },
  { time: "2018-12-22", value: 70.28, color: "#ff00ff" },
  { time: "2018-12-23", value: 49.29, color: "#ff0000" },
  { time: "2018-12-24", value: 40.64, color: "#ff0000" },
  { time: "2018-12-25", value: 57.46, color: "#ff0000" },
  { time: "2018-12-26", value: 50.55, color: "#0000ff" },
  { time: "2018-12-27", value: 34.85, color: "#0000ff" },
  { time: "2018-12-28", value: 56.68, color: "#0000ff" },
  { time: "2018-12-29", value: 51.6, color: "#00ff00" },
  { time: "2018-12-30", value: 75.33, color: "#00ff00" },
  { time: "2018-12-31", value: 54.85, color: "#00ff00" }
]);
```

## 数据格式

直方图系列的每个项目都应包括以下字段:

- `time` ([时间](./time.md)) - 时间
- `value` (`number`) - 值
- `color` (`string`, 可选) - 颜色

注意：如果未设置`color` ，则根据系列选项将直方图着色。

## 定制

可以使用以下选项自定义直方图系列:

| 名称    | 类型     | 默认值    | 描述                   |
| ------- | -------- | --------- | ---------------------- |
| `color` | `string` | `#26a69a` | 列颜色                 |
| `base`  | `number` | `0`       | 定义直方图列的初始级别 |

### 例子

- 设置直方图系列的初始选项:

  ```javascript
  const histogramSeries = chart.addHistogramSeries({
    color: "#FFF5EE",
    base: 5
  });
  ```

- 创建系列后更改选项:

  ```javascript
  // 例如，让我们覆盖默认初始级别:
  histogramSeries.applyOptions({
    base: -10
  });
  ```

## 下一步是什么

- [定制](./customization.md)
- [常量](./constants.md)
- [时间](./time.md)
