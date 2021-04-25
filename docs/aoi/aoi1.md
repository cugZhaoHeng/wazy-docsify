

## 接口详解

### 人口指数接口

```
https://lbi-api.newayz.com/openapi/v1/populationCount POST
```

请求参数

| 字段名 | 必选 | 类型              | 说明              |
| ------ | ---- | ----------------- | ----------------- |
| month  | 是   | string            | 月份，例：2021-01 |
| fences | 是   | list of `Polygon` | 围栏列表          |



[`Polygon`]

| 参数名    | 必选 | 类型             | 说明                                                         |
| --------- | ---- | ---------------- | ------------------------------------------------------------ |
| fenceCode | 是   | string           | 围栏类型，可选值：[circle，polygon]                          |
| radius    | 否   | integer          | 圆形半径，fenceCode选择circle时，必选                        |
| longitude | 否   | double           | 圆形中心经度，fenceCode选择circle时，必选                    |
| latitude  | 否   | double           | 圆形中心纬度，fenceCode选择circle时，必选                    |
| polygons  | 否   | list of double[] | polygon的顶点，每个元素都是经纬度二维数组，经度在前，维度在后，fenceCode选择polygon时，必选 |



### 请求示例 :id=request-example
| 参数名    | 必选 | 类型             | 说明                                                         |
| --------- | ---- | ---------------- | ------------------------------------------------------------ |
| fenceCode | 是   | string           | 围栏类型，可选值：[circle，polygon]                          |
| radius    | 否   | integer          | 圆形半径，fenceCode选择circle时，必选                        |
| longitude | 否   | double           | 圆形中心经度，fenceCode选择circle时，必选                    |
| latitude  | 否   | double           | 圆形中心纬度，fenceCode选择circle时，必选                    |
| polygons  | 否   | list of double[] | polygon的顶点，每个元素都是经纬度二维数组，经度在前，维度在后，fenceCode选择polygon时，必选 |