# 时间

本文包含表示时间数据项的类型说明。

## UNIX 时间戳

如果图表显示日内间隔，则应使用 UNIX 时间戳格式进行时间点数据传输。

请注意，为了防止错误，您应该在 TypeScript 代码中将时间的数字类型转换为`UTCTimestamp`类型（值应该转换为 UNIX 时间戳的值）。

例子:

```javascript
const timestamp = 1529884800; // 2018/06/25
```

## 营业日对象

此类型用于指定 DWM 数据的时间。

此格式使用年，月和日显示为单独字段的对象：

- `year` (`number`) - 年
- `month` (`number`) - 月
- `day` (`number`) - 日

例子:

```javascript
const day = { year: 2019, month: 6, day: 1 }; // 2019/06/01
```

## 营业日字符串

此格式比工作日格式短。它允许您使用 ISO 字符串格式指定日期(`YYYY-MM-DD`).

例子:

```javascript
const timestamp = "2018-06-25"; // 2018/06/25
```
