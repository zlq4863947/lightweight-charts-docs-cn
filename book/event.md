# 事件

事件订阅可以通过订阅鼠标单击/移动鼠标光标以及图表可见时间范围的更改，来通知您。

## Click

| 名称                                                  | 描述                           |
| ----------------------------------------------------- | ------------------------------ |
| `subscribeClick(handler: MouseEventHandler): void;`   | 当鼠标点击图表时，收到通知     |
| `unsubscribeClick(handler: MouseEventHandler): void;` | 当鼠标点击图表时，不会收到通知 |

例子:

```javascript
function handleClick(param) {
  if (!param.point) {
    return;
  }

  console.log(
    `An user clicks at (${param.point.x}, ${
      param.point.y
    }) point, the time is ${param.time}`
  );
}

chart.subscribeClick(handleClick);

// ... after some time

chart.unsubscribeClick(handleClick);
```

## 十字线移动

| 名称                                                          | 描述                             |
| ------------------------------------------------------------- | -------------------------------- |
| `subscribeCrosshairMove(handler: MouseEventHandler): void;`   | 鼠标在图表上移动时收到通知       |
| `unsubscribeCrosshairMove(handler: MouseEventHandler): void;` | 鼠标在图表上移动时，不会收到通知 |

例子:

```javascript
function handleCrosshairMoved(param) {
  if (!param.point) {
    return;
  }

  console.log(
    `A user moved the crosshair to (${param.point.x}, ${
      param.point.y
    }) point, the time is ${param.time}`
  );
}

chart.subscribeCrosshairMove(handleCrosshairMoved);

// ... after some time

chart.unsubscribeCrosshairMove(handleCrosshairMoved);
```

## 时间范围变更

| 名称                                                                             | 描述                                   |
| -------------------------------------------------------------------------------- | -------------------------------------- |
| `subscribeVisibleTimeRangeChange(handler: TimeRangeChangeEventHandler): void;`   | 当可见数据范围发生变化时，收到通知     |
| `unsubscribeVisibleTimeRangeChange(handler: TimeRangeChangeEventHandler): void;` | 当可见数据范围发生变化时，不会收到通知 |

## 类型

### MouseEventHandler

MouseEventHandler 是一种在订阅方法中使用的回调。

```typescript
export type MouseEventHandler = (param: MouseEventParams) => void;
```

`MouseEventParams` 是具有以下字段的对象:

- `time` (`Time`, 可选) - 时间
- `point`: (`{ x: number, y: number }`, 可选) - 坐标
- `seriesPrices`: (`Map<ISeriesApi, number | OHLC>`) - 系列价格

`time` 如果事件是在数据范围之外触发（例如，所有数据点的右/左），则不定义。

`point` 如果事件是在图表外部触发的（例如鼠标离开事件），则不定义。

`seriesPrices` 是一个对象，其中所有系列的价格都与事件点相对应。 对象属性是系列 API，值是价格。每个价格值是单值系列类型（线，面积，直方图）或 OHLC 结构的 k 线系列值。

### TimeRangeChangeEventHandler

TimeRangeChangeEventHandler 是一种回调，用于获取有关图表时间范围更改的通知。

```typescript
export type TimeRangeChangeEventHandler = (timeRange: TimeRange | null) => void;
```

`TimeRange` 是一个带有`from`和`to`字段的对象，它们是时间范围的第一个和最后一个时间点。

如果图表根本没有数据，则返回`null`。
