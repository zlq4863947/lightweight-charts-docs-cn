# 美国线图系列

美国线图以条形图显示价格变动。

条形的垂直线长度受限于最高价和最低价。

开盘价和收盘价分别由条形图的左侧和右侧的刻度线表示。

![美国线图示例](/images/bar-series.png "美国线图示例")

## 如何创建美国线图系列

```javascript
const barSeries = chart.addBarSeries({
  thinBars: false
});

// 设置数据
barSeries.setData([
  {
    time: "2018-12-19",
    open: 141.77,
    high: 170.39,
    low: 120.25,
    close: 145.72
  },
  {
    time: "2018-12-20",
    open: 145.72,
    high: 147.99,
    low: 100.11,
    close: 108.19
  },
  { time: "2018-12-21", open: 108.19, high: 118.43, low: 74.22, close: 75.16 },
  { time: "2018-12-22", open: 75.16, high: 82.84, low: 36.16, close: 45.72 },
  { time: "2018-12-23", open: 45.12, high: 53.9, low: 45.12, close: 48.09 },
  { time: "2018-12-24", open: 60.71, high: 60.71, low: 53.39, close: 59.29 },
  { time: "2018-12-25", open: 68.26, high: 68.26, low: 59.04, close: 60.5 },
  { time: "2018-12-26", open: 67.71, high: 105.85, low: 66.67, close: 91.04 },
  { time: "2018-12-27", open: 91.04, high: 121.4, low: 82.7, close: 111.4 },
  {
    time: "2018-12-28",
    open: 111.51,
    high: 142.83,
    low: 103.34,
    close: 131.25
  },
  { time: "2018-12-29", open: 131.33, high: 151.17, low: 77.68, close: 96.43 },
  { time: "2018-12-30", open: 106.33, high: 110.2, low: 90.39, close: 98.1 },
  { time: "2018-12-31", open: 109.87, high: 114.69, low: 85.66, close: 111.26 }
]);
```

## 数据格式

条形系列的每个项目都是[OHLC](./ohlc.md)项目。

## 定制

默认情况下，条形显示为每个宽 1 px 的细条。
通过禁用`thinBars`选项，条形宽度可以增加到 2px。

上涨和下跌条形的颜色必须单独设置。

可以使用以下选项自定义美国线图系列界面：

| 名称          | 类型      | 默认值    | 描述                              |
| ------------- | --------- | --------- | --------------------------------- |
| `thinBars`    | `boolean` | `true`    | 如果为 true，则条形表示为条形     |
| `upColor`     | `string`  | `#26a69a` | 上升条形颜色                      |
| `downColor`   | `string`  | `#ef5350` | 下降条形颜色                      |
| `openVisible` | `boolean` | `true`    | 如果为 true，则显示条形图的开放线 |

### 例子

- 设置条形系列的初始选项:

  ```javascript
  const barSeries = chart.addBarSeries({
    thinBars: false,
    upColor: "rgba(37, 148, 51, 0.2)",
    downColor: "rgba(191, 55, 48, 0.2)",
    openVisible: true
  });
  ```

- 创建系列后更改选项:

  ```javascript
  // 例如，让我们禁用细条和开放价格可见性
  barSeries.applyOptions({
    thinBars: false,
    openVisible: false
  });
  ```

## 下一步是什么

- [定制](./customization.md)
- [OHLC](./ohlc.md)
- [时间](./time.md)
