### POI周边客流接口

```
https://lbi-api.newayz.com/openapi/v2/poi/visitCount POST
```

查询以某个点为中心，覆盖到的单个grid或者9宫格客流数据。输出常驻人口数量、居民数量、职工数量、访问人数、访问频次

#### 请求参数

| 字段名   | 类型                                                         | 说明                                                         |      |
| -------- | ------------------------------------------------------------ | ------------------------------------------------------------ | ---- |
| pois     | array of [POI](https://document.newayz.com/p/6053124a1b4963000160f29a/60619ae3acf5270001aed28c#poi) |                                                              |      |
| relation | string                                                       | null                                                         |      |
| nearby   | string                                                       | 附近类型，jiugongge-九宫格，yigongge-一宫格，一个grid，默认九宫格 |      |
| limit    | string                                                       | 0                                                            |      |
| month    | string                                                       | 数据月份，格式202004，最早月份为当前月往前第14个月（包含当前月）；当前月的最后一天支持上个月数据（注意：此处的文档格式未通过，需采用格式yyMM如2101） |      |



[`POI`]

| 参数名 | 类型             | 说明                                 |      |
| ------ | ---------------- | ------------------------------------ | ---- |
| ids    | 未知             | 根据文档无法得出该字段类型，默认null |      |
| points | list of double[] | 中心坐标点                           |      |

#### 参数说明

请求示例，relation和ids默认为null可通过测试，limit为0，但是具体什么意思需要询问相关人员，此处注意month使用格式2101，具体参数获取需要真实条件提供

```
{
  "pois": {
    "ids": null,
    "points": [
      [
        121.602303,
        31.135994
      ]
    ]
  },
  "relation": null,
  "nearby": "jiugongge",
  "month": "2101",
  "limit": 0
}
```

#### 响应参数

| 字段名   | 类型    | 说明         |      |
| -------- | ------- | ------------ | ---- |
| living   | integer | 常驻人口数量 |      |
| resident | integer | 居民数量     |      |
| working  | integer | 职工数量     |      |
| user     | integer | 访问人数     |      |
| freq     | integer | 访问频次     |      |

#### 参数说明

输出人数

```
{
	"living": 2034,
	"freq": 50689,
	"working": 93,
	"user": 7902,
	"resident": 1952
}
```
