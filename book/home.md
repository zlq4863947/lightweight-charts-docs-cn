# 入门

## 安装

想使用 `lightweight-charts` 第一件要做的事是从[npm](https://www.npmjs.com/)下载并安装它。

`npm install --save lightweight-charts`

### 使用独立版本

使用此链接的[独立版本](https://unpkg.com/lightweight-charts@latest/dist/lightweight-charts.standalone.production.js)。
它已将全部的 ES Module 导入到`window.LightweightCharts`对象中。

## 创建第一个图表

### 在模块环境中

_注意：该软件包附带了 TypeScript 声明，因此可以在 TypeScript 代码中轻松使用`lightweight-charts`_

安装软件包后，只需将以下代码添加到 JavaScript 文件中：

```javascript
import { createChart } from "lightweight-charts";

const chart = createChart(document.body, { width: 400, height: 300 });
const lineSeries = chart.addLineSeries();
lineSeries.setData([
  { time: "2019-04-11", value: 80.01 },
  { time: "2019-04-12", value: 96.63 },
  { time: "2019-04-13", value: 76.64 },
  { time: "2019-04-14", value: 81.89 },
  { time: "2019-04-15", value: 74.43 },
  { time: "2019-04-16", value: 80.01 },
  { time: "2019-04-17", value: 96.63 },
  { time: "2019-04-18", value: 76.64 },
  { time: "2019-04-19", value: 81.89 },
  { time: "2019-04-20", value: 74.43 }
]);
```

### 在非模块环境中

1. 您需要确保在您要使用`lightweight-charts`的页面中添加了一个独立版本。

   只需在页面中添加`script`标签：

   ```html
   <script src="https://unpkg.com/lightweight-charts/dist/lightweight-charts.standalone.production.js"></script>
   ```

1. 将以下代码添加到网页（例如，将其添加到页面的 HTML 代码中的`script`标签）:

   ```javascript
   const chart = LightweightCharts.createChart(document.body, {
     width: 400,
     height: 300
   });
   const lineSeries = chart.addLineSeries();
   lineSeries.setData([
     { time: "2019-04-11", value: 80.01 },
     { time: "2019-04-12", value: 96.63 },
     { time: "2019-04-13", value: 76.64 },
     { time: "2019-04-14", value: 81.89 },
     { time: "2019-04-15", value: 74.43 },
     { time: "2019-04-16", value: 80.01 },
     { time: "2019-04-17", value: 96.63 },
     { time: "2019-04-18", value: 76.64 },
     { time: "2019-04-19", value: 81.89 },
     { time: "2019-04-20", value: 74.43 }
   ]);
   ```

   [JSFiddle](https://jsfiddle.net/TradingView/gemn0ud6/)

您的第一周图表以及准备就绪！

## 下一步是什么

- [数据列基础](./series-basics.md)
- [定制](./customization.md)
