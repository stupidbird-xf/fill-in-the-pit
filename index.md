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
