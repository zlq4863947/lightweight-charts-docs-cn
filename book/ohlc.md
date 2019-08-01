# OHLC

OHLC 是一种数据项。 它包括以下字段:

- `time` (`Time`) - 时间
- `open` (`number`) - 开盘价
- `high` (`number`) - 最高价
- `low` (`number`) - 最低价
- `close` (`number`) - 收盘价

此数据类型由多种系列类型使用，例如**美国线图**或**k 线图**。

## 例子

```javascript
const ohlcItem = {
  time: "2018-06-25",
  open: 10,
  high: 12,
  low: 9,
  close: 11
};
```
