# 定制

## 初始图表选项

创建图表时，可以设置图表的多数配置，之后可以通过`applyOptions` 动态修改配置。

### 大小

首先，创建图表时应设置首选图表大小:

```javascript
const chart = createChart(document.body, {
    width: 600,
    height: 380,
  },
});
```

如果要在调整网页大小时调整图表大小，请使用`resize`功能设置图表的宽度和高度:

```javascript
chart.resize(250, 150);
```

### 本地化

使用`localization`选项，您可以设置语音、日期和时间格式。

#### Locale

默认情况下，库使用浏览器语言设置。
因此，显示的日期和时间格式可以根据用户所在的区域而不同。
要为所有用户设置相同的语言设置，请使用`localization`选项的`locale`属性：

```javascript
const chart = createChart(document.body, {
  localization: {
    locale: "ja-JP"
  }
});
```

使用 `applyOptions` 方法，您可以在创建图表后动态更改区域设置:

```javascript
chart.applyOptions({
  localization: {
    locale: "en-US"
  }
});
```

#### 日期格式

可以使用`localization`选项的`dateFormat`属性设置首选日期格式。
可以使用的日期格式：:

- `dd MMM 'yy` - `25 Jun '18` _(默认)_
- `yyyy-MM-dd` - `2018-06-25`
- `yy-MM-dd` - `18-06-25`
- `yy/MM/dd` - `18/06/25`
- `yyyy/MM/dd` - `2018/06/25`
- `dd-MM-yyyy` - `25-06-2018`
- `dd-MM-yy` - `25-06-18`
- `dd/MM/yy` - `25/06/18`
- `dd/MM/yyyy` - `25/06/2018`
- `MM/dd/yy` - `06/25/18`
- `MM/dd/yyyy` - `06/25/2018`

```javascript
const chart = createChart(document.body, {
  localization: {
    dateFormat: "yyyy/MM/dd"
  }
});
```

#### 时间格式

`timeFormatter` 方法可以自定义垂直十字线下方的时间轴上显示的时间戳格式。
目前，无法更改时间刻度标签本身的时间格式，但此方法机会在未来使用。

```javascript
const chart = createChart(document.body, {
  localization: {
    timeFormatter: function() {
      return "Custom time format";
    }
  }
});
```

## 价格刻度

价格刻度是垂直坐标使用的价格数据值。

价格刻度有 4 种数据显示模式:

- `Normal`
- `Logarithmic`
- `Percentage`
- `Indexed to 100`

刻度本身可以位于系列的右侧/左侧。 如果您不希望它在图表上可见，请使用`position：none`。

以下为价格刻度可配置项:

| 名称             | 类型                                          | 默认值                      | 描述                                                                    |
| ---------------- | --------------------------------------------- | --------------------------- | ----------------------------------------------------------------------- |
| `position`       | `left` &#124; `right` &#124; `none`           | `right`                     | 设置价格刻度显示的位置                                                  |
| `mode`           | [价格刻度模式](./constants.md#pricescalemode) | `PriceScaleMode.Normal`     | 设置价格刻度的模式                                                      |
| `autoScale`      | `boolean`                                     | `true`                      | 如果为 true，则将系列数据缩放为图表大小                                 |
| `invertScale`    | `boolean`                                     | `false`                     | 如果为 true，在图表系列将垂直显示，一次增长趋势显示为下降趋势，反之亦然 |
| `alignLabels`    | `boolean`                                     | `true`                      | 如果为 true，则带有价格数据的标签不会重叠                               |
| `borderVisible`  | `boolean`                                     | `true`                      | 如果为 true，则可以看到价格刻度的边框                                   |
| `borderColor`    | `string`                                      | `#2b2b43`                   | 价格刻度的边框颜色                                                      |
| `scaleMargins`   | `{ bottom, top }`                             | `{ bottom: 0.1, top: 0.2 }` | 设置顶部和底部图表边框的系列边距（百分比）                              |
| `entireTextOnly` | `boolean`                                     | `false`                     | 如果为 false，即使它们部分不可见，也会显示顶角和底角标签                |

### 价格刻度定制的例子

```javascript
chart.applyOptions({
  priceScale: {
    position: "left",
    mode: 2,
    autoScale: false,
    invertScale: true,
    alignLabels: false,
    borderVisible: false,
    borderColor: "#555ffd",
    scaleMargins: {
      top: 0.3,
      bottom: 0.25
    }
  }
});
```

## 时间刻度

时间刻度是横向坐标使用的时间数据值。

时间刻度选项可以在缩放和调整图表大小时调整图表上显示的系列。

如果需要，可以隐藏时间刻度。

以下为时间刻度可配置项:

| 名称                           | 类型      | 默认值    | 描述                                                                        |
| ------------------------------ | --------- | --------- | --------------------------------------------------------------------------- |
| `rightOffset`                  | `number`  | `0`       | 设置 k 线的右侧边距宽度                                                     |
| `barSpacing`                   | `number`  | `6`       | 以像素为单位设置 K 线之间的间距                                             |
| `fixLeftEdge`                  | `boolean` | `false`   | 如果为 true，则阻止滚动到第一个 K 线的左侧                                  |
| `lockVisibleTimeRangeOnResize` | `boolean` | `false`   | 如果为 true，则在图表大小调整期间阻止更改可见时间区域                       |
| `rightBarStaysOnScroll`        | `boolean` | `false`   | 如果为 false，则滚动时与悬停的 k 线保持在同一位置                           |
| `borderVisible`                | `boolean` | `true`    | 如果为 true，则可以看到时间刻度边框                                         |
| `borderColor`                  | `string`  | `#2b2b43` | 时间刻度的边框颜色                                                          |
| `visible`                      | `boolean` | `true`    | 如果为 true，则时间刻度显示在图表上                                         |
| `timeVisible`                  | `boolean` | `false`   | 如果为 true，则时间刻度和十字准线垂直标签上显示时间                         |
| `secondsVisible`               | `boolean` | `true`    | 如果为 true，则在日内间隔以`hh:mm:ss`格式的时间显示在十字准线垂直线的标签上 |

### 时间刻度定制的例子

```javascript
chart.applyOptions({
  timeScale: {
    rightOffset: 12,
    barSpacing: 3,
    fixLeftEdge: true,
    lockVisibleTimeRangeOnResize: true,
    rightBarStaysOnScroll: true,
    borderVisible: false,
    borderColor: "#fff000",
    visible: true,
    timeVisible: true,
    secondsVisible: false
  }
});
```

## 十字线

十字准线显示图表上任何悬停点的价格轴和时间轴值的交集。

它由水平和垂直线表示。 如果需要，可以通过设置`color`，`width`和`style`或者使用`visible`选项来禁用它们中的每一个。 请注意，禁用十字准线不会禁用`线`和`面积`系列上的十字准线标记。 可以使用相关系列的`crosshairMarkerVisible`选项禁用它。

十字准线的垂直和水平线在价格和时间轴上的所有标记。 都可以被禁用。

Crosshair 有两种移动模式:

- `Magnet` 模式，默认情况下启用的模式，将十字线的水平线吸到到价格线、或 k 线的收盘价上。
- `Normal` 模式,让十字准线在图表中自由移动。

请注意，十字线必须单独定制。

以下为十字线可配置项:

| 名称                   | 类型                                          | 默认值                 | 描述                                    |
| ---------------------- | --------------------------------------------- | ---------------------- | --------------------------------------- |
| `color`                | `string`                                      | `#758696`              | 十字线颜色                              |
| `width`                | `number`                                      | `1`                    | 十字线宽度，以像素为单位                |
| `style`                | [LineStyle](./constants.md#linestyle)         | `LineStyle.Dashed`     | 十字线样式                              |
| `visible`              | `boolean`                                     | `true`                 | 如果为 true，则在图表上显示十字线       |
| `labelVisible`         | `boolean`                                     | `true`                 | 如果为 true，则显示数据标签在相关刻度上 |
| `labelBackgroundColor` | `string`                                      | `#4c525e`              | 十字准线标签背景颜色                    |
| `mode`                 | [CrosshairMode](./constants.md#crosshairmode) | `CrosshairMode.Magnet` | 设置十字线移动的模式。                  |

### 十字线定制的例子

```javascript
chart.applyOptions({
  crosshair: {
    vertLine: {
      color: "#6A5ACD",
      width: 0.5,
      style: 1,
      visible: true,
      labelVisible: false
    },
    horzLine: {
      color: "#6A5ACD",
      width: 0.5,
      style: 0,
      visible: true,
      labelVisible: true
    },
    mode: 1
  }
});
```

## 网格

通过在价格和时间轴的可见标记的水平处绘制的垂直和水平线，在图表背景中表示 网格。
可以为 网格线设置自定义`color`和`style`，或者在必要时禁用它们的可见性。
请注意，网格的垂直和水平线必须单独定制。

以下为网格可配置项：

| 名称      | 类型                                  | 默认值            | 描述                                |
| --------- | ------------------------------------- | ----------------- | ----------------------------------- |
| `color`   | `string`                              | `#d6dcde`         | 网格线颜色                          |
| `style`   | [LineStyle](./constants.md#linestyle) | `LineStyle.Solid` | 网格线样式                          |
| `visible` | `boolean`                             | `true`            | 如果为 true，则网格线将显示在图表上 |

### 网格定制的例子

```javascript
chart.applyOptions({
  grid: {
    vertLines: {
      color: "rgba(70, 130, 180, 0.5)",
      style: 1,
      visible: true
    },
    horzLines: {
      color: "rgba(70, 130, 180, 0.5)",
      style: 1,
      visible: true
    }
  }
});
```

## 水印

水印是背景标签，其包括所绘制数据的简要描述。可以添加任何文本。
默认情况下禁用水印显示。
请确保启用它并设置适当的字体颜色和大小，以使水印在图表的背景中可见。
我们建议使用半透明颜色和大字体。
另请注意，水印位置可以垂直和水平对齐。

以下为水印可配置项:

| 名称        | 类型                                  | 默认值             | 描述                            |
| ----------- | ------------------------------------- | ------------------ | ------------------------------- |
| `color`     | `string`                              | `rgba(0, 0, 0, 0)` | 水印颜色                        |
| `visible`   | `boolean`                             | `false`            | 如果为 true，则水印显示在图表上 |
| `text`      | `string`                              | `''`               | 包含要在水印中显示的文本        |
| `fontSize`  | `number`                              | `48`               | 水印的字体大小（以像素为单位）  |
| `horzAlign` | `left` &#124; `center` &#124; `right` | `center`           | 水印水平对齐位置                |
| `vertAlign` | `top` &#124; `center` &#124; `bottom` | `center`           | 水印垂直对齐位置                |

### 水印定制的例子

```javascript
chart.applyOptions({
  watermark: {
    color: "rgba(11, 94, 29, 0.4)",
    visible: true,
    text: "TradingView Watermark Example",
    fontSize: 24,
    horzAlign: "left",
    vertAlign: "bottom"
  }
});
```

## 图表布局选项

以下选项可用于自定义图表设计:

| 名称              | 类型     | 默认值                                       | 描述                     |
| ----------------- | -------- | -------------------------------------------- | ------------------------ |
| `backgroundColor` | `string` | `#ffffff`                                    | 图表和刻度的背景颜色     |
| `textColor`       | `string` | `#191919`                                    | 刻度的文本颜色           |
| `fontSize`        | `number` | `11`                                         | 刻度值的字体大小         |
| `fontFamily`      | `string` | `'Trebuchet MS', Roboto, Ubuntu, sans-serif` | 在刻度上使用 family 字体 |

### 布局自定义的例子

```javascript
chart.applyOptions({
  layout: {
    backgroundColor: "#FAEBD7",
    textColor: "#696969",
    fontSize: 12,
    fontFamily: "Calibri"
  }
});
```

## 滚动和缩放选项

默认情况下，系列和刻度的滚动和缩放模式处于启用状态。
您可以使用`handleScroll`和`handleScale`选项禁用它们中的任何一个。

### 滚动选项

| 名称               | 类型      | 默认值 | 描述                                                                                                                                                                                               |
| ------------------ | --------- | ------ | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `mouseWheel`       | `boolean` | `true` | 如果为 true，则启用使用水平鼠标滚轮的图表滚动                                                                                                                                                      |
| `pressedMouseMove` | `boolean` | `true` | 如果为 true，则允许按下鼠标左键滚动图表                                                                                                                                                            |
| `horzTouchDrag`    | `boolean` | `true` | 如果为 true，则图表处理触摸屏上的水平指针移动。 在这种情况下，网页不会滚动。 如果将其设置为 false，则会滚动网页。 请记住，如果用户开始垂直或水平滚动图表，则向任何方向继续滚动，直到用户松开手指   |
| `vertTouchDrag`    | `boolean` | `true` | 如果为 true，则图表处理触摸屏上的垂直指针移动。 在这种情况下，网页不会滚动。 如果将其设置为 false，则会滚动网页。 请记住，如果用户开始垂直或水平滚动图表，则向任何方向继续滚动，直到用户松开手指。 |

### 缩放选项

| 名称                   | 类型      | 默认值 | 描述                                                                 |
| ---------------------- | --------- | ------ | -------------------------------------------------------------------- |
| `axisPressedMouseMove` | `boolean` | `true` | 如果为 true，则允许按下鼠标左键进行刻度缩放                          |
| `mouseWheel`           | `boolean` | `true` | 如果为 true，则启用使用鼠标滚轮进行系列缩放                          |
| `pinch`                | `boolean` | `true` | 如果为 true，则启用使用捏合/缩放手势的系列缩放（触摸设备支持此选项） |

### 滚动/缩放自定义的例子

```javascript
chart.applyOptions({
  handleScroll: {
    mouseWheel: true,
    pressedMouseMove: true
  },
  handleScale: {
    axisPressedMouseMove: true,
    mouseWheel: true,
    pinch: true
  }
});
```
