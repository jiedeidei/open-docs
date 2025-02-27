
# 简介
图片。支持 JPG、PNG、SVG、WEBP（iOS 不支持动图）、GIF 等格式。

## 使用限制
使用 webview 嵌套 H5 时，若遇到图片资源不显示问题，可参考 [配置 H5 白名单流程](https://opendocs.alipay.com/mini/component/idfvg6) 获取 H5 页面中所有的域名地址（含图片静态资源的地址），全部加入域名白名单中。

## 扫码体验
![|127x157](https://gw.alipayobjects.com/zos/skylark-tools/public/files/66539db61b570eb2b7cf2df4241ea56c.png#align=left&display=inline&height=157&margin=%5Bobject%20Object%5D&originHeight=157&originWidth=127&status=done&style=none&width=127)

# 使用

## Herbox
[小程序在线](https://herbox-embed.alipay.com/s/doc-image?theme=light&previewZoom=75&chInfo=openhome-doc) 

## 示例代码

### .axml 示例代码
```html
<!-- API-DEMO page/component/image/image.axml -->
<view class="page">
  <view class="page-description">图片</view>
  <view class="page-section" a:for="{{array}}" a:for-item="item">
    <view class="page-section-title">{{item.text}}</view>
    <view class="page-section-demo" onTap="onTap">
      <image class="image"
        data-name="{{item.mode}}"
        onTap="onTap"
        mode="{{item.mode}}" src="{{src}}" onError="imageError" onLoad="imageLoad" />
    </view>
  </view>
</view>
```

### .js 示例代码
```javascript
// API-DEMO page/component/image/image.js
Page({
  data: {
    array: [{
      mode: 'scaleToFill',
      text: 'scaleToFill：不保持纵横比缩放图片，使图片完全适应',
    }, {
      mode: 'aspectFit',
      text: 'aspectFit：保持纵横比缩放图片，使图片的长边能完全显示出来',
    }, {
      mode: 'aspectFill',
      text: 'aspectFill：保持纵横比缩放图片，只保证图片的短边能完全显示出来',
    }, {
      mode: 'widthFix',
      text: 'widthFix：宽度不变，高度自动变化，保持原图宽高比不变',
    }, {
      mode: 'top',
      text: 'top：不缩放图片，只显示图片的顶部区域',
    }, {
      mode: 'bottom',
      text: 'bottom：不缩放图片，只显示图片的底部区域',
    }, {
      mode: 'center',
      text: 'center：不缩放图片，只显示图片的中间区域',
    }, {
      mode: 'left',
      text: 'left：不缩放图片，只显示图片的左边区域',
    }, {
      mode: 'right',
      text: 'right：不缩放图片，只显示图片的右边边区域',
    }, {
      mode: 'top left',
      text: 'top left：不缩放图片，只显示图片的左上边区域',
    }, {
      mode: 'top right',
      text: 'top right：不缩放图片，只显示图片的右上边区域',
    }, {
      mode: 'bottom left',
      text: 'bottom left：不缩放图片，只显示图片的左下边区域',
    }, {
      mode: 'bottom right',
      text: 'bottom right：不缩放图片，只显示图片的右下边区域',
    }],
    src: '/image/ant.png',
  },
  imageError(e) {
    console.log('image 发生 error 事件，携带值为', e.detail.errMsg);
  },
  onTap(e) {
    console.log('image 发生 tap 事件', e);
  },
  imageLoad(e) {
    console.log('image 加载成功', e);
  },
});
```

### .acss 示例代码
```css
/* API-DEMO page/component/image/image.acss */
.page-section-demo {
  display: flex;
  justify-content: space-around;
}
.image {
  background-color: red;
  width: 100px;
  height: 100px;
}
```

## 属性
| **属性** | **类型** | **描述** |
| --- | --- | --- |
| src | String | 图片地址。 |
| mode | String | 图片模式。<br />**默认值：** scaleToFill |
| class | String | 外部样式。 |
| style | String | 内联样式。 |
| lazy-load | Boolean | 支持图片懒加载，不支持通过 css 来控制 image 展示隐藏的场景。<br />**默认值：** false<br />**版本要求：** 基础库 [1.9.0](https://opendocs.alipay.com/mini/framework/compatibility) 及以上 |
| default-source | String | 默认图片地址，若设置默认图片地址，会先显示默认图片，等 src 对应的图片加载成功后，再渲染对应的图片。<br />**版本要求：** 基础库 [1.19.0](https://opendocs.alipay.com/mini/framework/compatibility) 及以上 |
| onLoad | EventHandle | 图片载入完毕时触发，事件对象 `event.detail = {height: '图片高度px', width: '图片宽度px'}`。 |
| onError | EventHandle | 当图片加载错误时触发，事件对象 `event.detail = {errMsg: 'something wrong'`。 |
| onTap | EventHandle | 点击图片时触发。 |
| catchTap | EventHandle | 点击图片时触发，阻止事件冒泡。 |

**注意**：image 组件默认宽度 300px、高度 225px。

### mode
mode 有 14 种模式，其中 5 种是缩放模式，9 种是裁剪模式。

#### 缩放模式
| **属性** | **描述** |
| --- | --- |
| scaleToFill | 不保持纵横比缩放，使图片的宽高完全拉伸至填满 image 元素。 |
| aspectFit | 保持纵横比缩放，使图片的长边能完全显示出来。也就是说，可以完整地将图片显示出来。 |
| aspectFill | 保持纵横比缩放，只保证图片的短边能完全显示出来。也就是说，图片通常只在水平或垂直方向是完整的，另一个方向将会发生截取。 |
| widthFix | 宽度不变，高度自动变化，保持原图宽高比不变。 |
| heightFix | 高度不变，宽度自动变化，保持原图宽高比不变。<br />**版本要求**：基础库 [2.7.0 ](https://opendocs.alipay.com/mini/framework/compatibility)及以上 |


#### 裁剪模式
| **属性** | **描述** |
| --- | --- |
| top | 不缩放图片，只显示顶部区域。 |
| bottom | 不缩放图片，只显示底部区域。 |
| center | 不缩放图片，只显示中间区域。 |
| left | 不缩放图片，只显示左边区域。 |
| right | 不缩放图片，只显示右边区域。 |
| top left | 不缩放图片，只显示左上边区域。 |
| top right | 不缩放图片，只显示右上边区域。 |
| bottom left | 不缩放图片，只显示左下边区域。 |
| bottom right | 不缩放图片，只显示右下边区域。 |

**说明**：图片高度不能设置为 auto，如果需要图片高度为 auto，直接设置 mode 为 widthFix。

# FAQ

### image 标签支持读取流文件吗？ 
小程序中显示二进制数据流的图片，需要先将二进制数据转成 base64 字符串，然后把 base64 字符串放在 image 中的 src 中实现显示。

### 真机调用 image 组件，显示的图片被压缩？
建议把 mode 值设为 widthFix。

# 相关文档

- [my.chooseImage](https://opendocs.alipay.com/mini/api/media/image/my.chooseimage)<br />
- [my.compressImage](https://opendocs.alipay.com/mini/api/media/image/my.compressimage)<br />
- [my.getImageInfo](https://opendocs.alipay.com/mini/api/media/image/my.getimageinfo)<br />
- [my.previewImage](https://opendocs.alipay.com/mini/api/media/image/my.previewimage)<br />
- [my.saveImage](https://opendocs.alipay.com/mini/api/media/image/my.saveimage)<br />
