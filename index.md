#### 1、vue项目 元素绑定change事件，点击别的元素容易多次触发

> 解决办法  @click.native  监听根元素的原生事件 

#### 2、子元素触发事件阻止事件冒泡

> 解决办法 @click.stop

#### 3、微信分享的问题

> 获取微信签名信息的接口传的url必须是完整的页面url

> 微信分享的时候url不可以带中文

#### 4、vue动画执行之后每次结束弹出的弹窗都会乱

> 事件监听，每次执行之后清除事件监听

#### 5、vue 项目用<template></>template>

> template不是真正的dom元素，编译之后不显示dom 循环的时候不能带key

> 解决 key放在template 里面的子元素上

#### 6、vue-cli3 一直运行 /sockjs-node/info?t= 解决方案

> 如果你的项目没有用到 sockjs，vuecli3 运行 npm run serve 之后 network 里面一直调研一个接口：http://localhost:8080/sockjs-node/info?t=1462183700002

> 1. 找到/node_modules/sockjs-client/dist/sockjs.js 

> 2. 找到代码的 1605行  
  try {
  //  self.xhr.send(payload); 把这里注掉
  } catch (e) {
    self.emit('finish', 0, '');
    self._cleanup(false);
  }

#### 7、 vue项目有的时候接口成功，但是后台得不到数据

> 原因：axios 发送post请求 当参数为对象时，参数在request payload里，content-type为application/json;charset=UTF-8，这样springmvc是不能通过

> 解决： 修改axios请求头 headers: {
      'Content-Type': type || 'application/x-www-form-urlencoded'
    }

#### 8、vue 解决页面v-for中修改item属性值后页面v-if不改变的问题

> 原因：层级嵌套的太多

> this.$forceUpdate();

#### 9、用vue重构的时候调用之前的接口范湖时间变成毫秒数了，之前返回是时间格式

> 请求端可以通过accept设置后端返回的数据类型 axios 默认accept 是application/json, text/plain, */*

> headers: {
    'Accept': '*/*'
  },

#### 10、swiper onClick绑定事件手动滑动之后事件失效

> swiper框架复制的slide没有复制click事件，所以click失效 

> 解决办法： 在现有的dom上绑定动态属性如（:name="slide.name"），利用new Swiper时绑定事件如： option{on: {click(e) {consoe.log(e.target.name)}}}

#### 11、安卓手机调用微信扫一扫问题 在APP.vue里面config 但是页面里面调用扫一扫接口没有反应

> 安卓手机需要在router 导航守卫全局后置钩子afterEach里面config

#### ElementUI dialog初始化获取不到元素

> Vue+ElementUI开发项目，使用Dialog作为子组件时，父组件初始化子组件内部未能获取到dom元素

> + slot="footer"

#### 12、文本超出省略

> 单行文本超出省略： 
  overflow: hidden;
  text-overflow:ellipsis;
  white-space: nowrap;

> 多行文本超出省略
  overflow: hidden;
  text-overflow: ellipsis;
  display: -webkit-box;
  -webkit-line-clamp: 2; // 行数
  -webkit-box-orient: vertical;

> 注意： 多行文本超出省略 样式元素不可加padding-bottom