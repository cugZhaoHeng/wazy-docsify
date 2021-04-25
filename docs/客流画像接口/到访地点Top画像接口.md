### 到访地点Top画像接口

```
https://lbi-api.newayz.com/openapi/v1/crowdProfile/addrTop POST
```

该接口可查询任意围栏范围内的到总客流、到访人口、常驻人口、工作人口、居住人口的线下到访地点Top画像情况

#### 请求参数

| 字段名 | 必选 | 类型              | 说明              |
| ------ | ---- | ----------------- | ----------------- |
| month  | 是   | string            | 月份，例：2021-01 |
| fences | 是   | list of `Polygon` | 围栏列表          |



[`Polygon`]

| 参数名     | 必选 | 类型             | 说明                                                         |
| ---------- | ---- | ---------------- | ------------------------------------------------------------ |
| fenceCode  | 是   | string           | 围栏类型，可选值：[circle，polygon]                          |
| radius     | 否   | integer          | 圆形半径，fenceCode选择circle时，必选                        |
| longitude  | 否   | double           | 圆形中心经度，fenceCode选择circle时，必选                    |
| latitude   | 否   | double           | 圆形中心纬度，fenceCode选择circle时，必选                    |
| polygons   | 否   | list of double[] | polygon的顶点，每个元素都是经纬度二维数组，经度在前，维度在后，fenceCode选择polygon时，必选 |
| filterType | 是   | string           | 过滤类型，必选，可选值：[all，resident，living，working，visiting]，all-筛选所有出现的人, resident-筛选常驻在此地的人（工作或居住），living-筛选居住在此地的人，working-筛选工作在此地的人，visiting-筛选临时到访人群 |

#### 参数说明

请求示例，此处较上两个接口多提供了一个参数：filterType，用于筛选，fenceCode为polygon(多边形围栏)和circle(圆围栏)共同入参，也可以单独入参，具体参数获取需要真实条件提供

```
{
	"month": "2021-01",
	"fences": [
	{
      "fenceCode": "circle",
      "radius": 1000,
      "longitude": 120.475595,
      "latitude": 31.21652
    },{
		"fenceCode": "polygon",
		"polygons": [
			[121.127789, 31.041503],
			[121.115086, 31.034811],
			[121.117661, 31.025176],
			[121.124356, 31.026721],
			[121.124871, 31.022823],
			[121.133025, 31.023558],
			[121.137831, 31.005315],
			[121.141608, 31.00583],
			[121.144955, 30.996119],
			[121.152251, 30.99759],
			[121.15371, 30.992293],
			[121.158688, 30.993544],
			[121.153796, 31.011862],
			[121.142638, 31.031134],
			[121.137917, 31.042239],
			[121.130536, 31.038415]
		]
	}]
}
```

#### 响应参数

| 字段名             | 必选 | 类型           | 说明     |
| ------------------ | ---- | -------------- | -------- |
| residentialQuarter | 是   | list of `Item` | 居住小区 |
| workingArea        | 是   | list of `Item` | 工作小区 |
| frequentMall       | 是   | list of `Item` | 常去商场 |
| sourceCity         | 是   | list of `Item` | 来源城市 |
| sourceProvince     | 是   | list of `Item` | 来源省份 |

#### 参数说明

每个item包括名称、id和比率（java中用BigDecimal接收）

```
{
	"gender": [{
		"name": "女",
		"id": "25",
		"ratio": 0.56
	}, {
		"name": "男",
		"id": "24",
		"ratio": 0.44
	}],
	"housePrice": [{
		"name": "普通社区",
		"id": "90",
		"ratio": 0.7429
	}, {
		"name": "高档社区",
		"id": "89",
		"ratio": 0.1068
	}, {
		"name": "豪宅社区",
		"id": "88",
		"ratio": 0.1014
	}, {
		"name": "别墅",
		"id": "91",
		"ratio": 0.049
	}],
	"consumption": [{
		"name": "消费_低",
		"id": "145",
		"ratio": 0.496
	}, {
		"name": "消费_中",
		"id": "146",
		"ratio": 0.2615
	}, {
		"name": "消费_高",
		"id": "147",
		"ratio": 0.2425
	}],
	"carAssets": [{
		"name": "有车",
		"id": "148",
		"ratio": 0.0804
	}],
	"children": [{
		"name": "6-12岁小孩",
		"id": "43",
		"ratio": 0.4528
	}, {
		"name": "3-6岁小孩",
		"id": "42",
		"ratio": 0.3039
	}, {
		"name": "0-3岁小孩",
		"id": "41",
		"ratio": 0.1844
	}, {
		"name": "12-18岁小孩",
		"id": "44",
		"ratio": 0.0588
	}, {
		"name": "备孕",
		"id": "39",
		"ratio": 0
	}, {
		"name": "孕期",
		"id": "40",
		"ratio": 0
	}],
	"operators": [{
		"name": "中国移动",
		"id": "21",
		"ratio": 0.5612
	}, {
		"name": "中国电信",
		"id": "23",
		"ratio": 0.2609
	}, {
		"name": "中国联通",
		"id": "22",
		"ratio": 0.1779
	}],
	"marriage": [{
		"name": "已婚",
		"id": "38",
		"ratio": 0.601
	}],
	"age": [{
		"name": "26-35",
		"id": "28",
		"ratio": 0.5171
	}, {
		"name": "36-45",
		"id": "29",
		"ratio": 0.2093
	}, {
		"name": "19-25",
		"id": "27",
		"ratio": 0.2012
	}, {
		"name": "46-55",
		"id": "30",
		"ratio": 0.0345
	}, {
		"name": "19岁以下",
		"id": "32",
		"ratio": 0.0311
	}, {
		"name": "55岁以上",
		"id": "31",
		"ratio": 0.0067
	}]
}
```


