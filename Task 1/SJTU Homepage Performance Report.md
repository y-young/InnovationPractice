## SJTU Homepage Performance  Report

### 概述

禁用缓存时：传输数据量 15.2MB，资源总大小 16.6MB，加载完成时间：7.62s

启用缓存时：传输数据量 11.3MB，资源总大小 16.6MB，加载完成时间：3.05s

### 图片大小过大

例如：https://www.sjtu.edu.cn/resource/upload/202011/20201103_023859_338.png 大小超过 1MB，加载耗时超过 700ms

建议：

1. 减小图片大小，如降低位深度(tinypng.com)，降低分辨率
2. 使用新一代图片格式，如webp

### 不可见图片使用同步加载

建议：对于不在显示区域内的图片使用 lazyload

### HTTP/1.1

建议：使用 HTTP/2，HTTP/2 相较于 HTTP/1.1 有更多性能提升

### 外部资源阻塞主线程渲染

https://www.sjtu.edu.cn/resource/assets/plugin/OwlCarousel/owl.carousel.css

建议：对于非关键资源使用异步加载

### 未使用资源 preload

建议：对于关键请求使用 preload，如 https://www.sjtu.edu.cn/resource/assets/css/iconfont.css

### 静态资源未使用缓存

建议：对于静态资源，如图片，js，css使用缓存，以降低二次访问加载时间

### DOM 元素大小过大

建议：降低元素嵌套深度，减少子元素数量，以降低渲染时的内存占用

### 图片元素未设定占位宽度和高度

此类图片未加载时浏览器无法计算占位，而加载完毕后布局需要重新计算，可能引起布局抖动，如首页轮播图

建议：显式指定图片元素的宽度和高度