# K-Report

# 思路

K-Report主要的功能点

1. 网络分析: 

  1. 首屏计算时间
  2. JS,css资源加载时间
2. 错误分析

# 首屏时间

`above the fold`

首屏时间主要经历的阶段

`开始请求 --(1)--首字节时间 --(2)-- 开始渲染时间--(3)--  首屏栈`

1. 浏览器请求文档,需要经过`blocking、proxying、dns
lookup、connecting、sending、waiting`
2. 加载完毕head中的css,也可以理解为加载完head标签 
3. 开始渲染时间
4. 首屏栈

如何获取这些关键点的时间

1. 首字节时间: `HTML5 performance API`提供
2. 开始渲染时间: 这个是解析完毕head或刚开始解析body开始,这个需要在标签里主动去埋
3. 首屏栈: 

  1. 绑定class,因为background-img这里load事件是无法捕抓的,所以绑定好class,我们主动搜索它包含的资源,然后获取url和performance的资源url比较
  2. 不绑定class,我们只能保守的遍历所有有可能在首屏的元素,然后逐一判断资源url




# 参考链接

1. 关于首屏时间: http://hushicai.com/2014/04/19/guan-yu-ye-mian-shou-ping-shi-jian.html