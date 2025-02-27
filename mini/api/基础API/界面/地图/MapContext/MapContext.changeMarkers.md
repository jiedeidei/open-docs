
# 简介
**MapContext.changeMarkers** 用于添加、删除、更新指定的标记（marker）。

## 使用限制

- 基础库 [1.23.0](https://opendocs.alipay.com/mini/framework/lib) 或更高版本；支付宝客户端 10.1.82 或更高版本，若版本较低，建议采取 [兼容处理](https://opendocs.alipay.com/mini/framework/compatibility)。
- 此 API 支持个人支付宝小程序、企业支付宝小程序使用。

# 接口调用

## 示例代码
```javascript
// .js
this.mapCtx = my.createMapContext('map');

this.mapCtx.changeMarkers({
  add:[{
      iconPath: "/image/green_tri.png",
      id: 10,
      latitude: 30.279383,
      longitude: 120.131441,
      width: 50,
      height: 50
    },{
      iconPath: "/image/green_tri.png",
      id: 10,
      latitude: 30.279383,
      longitude: 120.131441,
      width: 50,
      height: 50,
      customCallout: {
        type: 1,
        time: '1',
      },
      fixedPoint:{
        originX: 400,
        originY: 400,
      },
      iconAppendStr: '黄龙时代广场黄龙时代广场黄龙时代广场黄龙时代广场test'
    }],
  success: res => {
    console.log(res);
  }
});
```

## 入参
| **属性** | **类型** | **描述** |
| --- | --- | --- |
| add | Array | 需要添加的 marker 数组。 |
| remove | Array | 需要删除的 marker 数组。 |
| update | Array | 需要更新的 marker 数组。 |


### Array 数组对象
请参考 Marker 对象: [markers](https://opendocs.alipay.com/mini/component/map#markers)。
