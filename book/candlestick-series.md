# K 线图系列

K 线图显示蜡烛形式的价格变动。

在 K 线图表中,开盘价和收盘价形成的蜡烛实体，而上引线和下引线分别代表最高价和最低价。

![K 线图示例](/images/candlestick-series.png "K 线图示例")

## 如何创建 K 线图系列

```javascript
const candlestickSeries = chart.addCandlestickSeries();

// 设置数据
candlestickSeries.setData([
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

K 线系列的每个项目都是[OHLC](./ohlc.md)项目。

## 定制

上涨和下跌的 k 线的颜色必须单独设置。

K 线边框和 K 线默认可见，可以禁用。
请注意，当禁用 K 线时，K 线不会显示最高价和最低价。
边框和 K 线颜色可以同时为所有 K 线设置，也可以分别为上涨和下跌 K 线设置。 如果后者是您的首选，请确保您不使用常用选项，例如`borderColor`和`wickColor`，因为它们与指定的优先级相比具有更高的优先级。

K 线系列有以下选项可以自定义:
| 名称 | 类型 | 默认值 | 描述 |
| ----------------- | --------- | --------- | --------------------------------------------------------------- |
| `upColor` | `string` | `#26a69a` | 上涨的 k 线颜色 |
| `downColor` | `string` | `#ef5350` | 下跌的 k 线颜色 |
| `borderVisible` | `boolean` | `true` | 如果为 true，则绘制 k 线的边框 |
| `wickVisible` | `boolean` | `true` | 如果为 true，以最高价和最低价显示 k 线的烛芯 |
| `borderColor` | `string` | `#378658` | 所有 k 线系列的边界颜色 |
| `wickColor` | `string` | `#737375` | 全部 k 线系列的烛芯颜色 |
| `borderUpColor` | `string` | `#26a69a` | 上涨的 k 线边框颜色 |
| `borderDownColor` | `string` | `#ef5350` | 下跌的 k 线边框颜色 |
| `wickUpColor` | `string` | `#26a69a` | 上涨的 k 线烛芯颜色 |
| `wickDownColor` | `string` | `#ef5350` | 下跌的 k 线烛芯颜色 |

### 例子

- 设置 K 线系列的初始选项:

  ```javascript
  const candlestickSeries = chart.addCandleSeries({
    upColor: "#6495ED",
    downColor: "#FF6347",
    borderVisible: false,
    wickVisible: true,
    borderColor: "#000000",
    wickColor: "#000000",
    borderUpColor: "#4682B4",
    borderDownColor: "#A52A2A",
    wickUpColor: "#4682B4",
    wickDownColor: "#A52A2A"
  });
  ```

- 创建系列后更改选项:

  ```javascript
  // 例如，让我们覆盖蜡烛的上涨下跌颜色
  candlestickSeries.applyOptions({
    upColor: "rgba(255, 0, 0, 1)",
    downColor: "rgba(0, 255, 0, 1)"
  });
  ```

## 下一步是什么

- [定制](./customization.md)
- [OHLC](./ohlc.md)
- [时间](./time.md)
