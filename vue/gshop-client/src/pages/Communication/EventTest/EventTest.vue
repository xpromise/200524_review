<template>
  <div>
    <h1>EventTest组件</h1>
    <!-- 
    原生DOM事件
        绑定原生DOM事件监听的2种情况
            在html标签上绑定DOM事件名的监听
            在组件标签上绑定DOM事件名的监听(.native), 事件绑定在组件的根标签上
        当用户操作对应的界面时, 浏览器就会自动创建并封闭包含相关数据的事件对象, 分发对应的事件, 从而触发事件监听回调函数调用
        事件对象event, 本质是 "事件数据对象"
        event对象内的数据属性: target / offsetX / offsetY / keyCode等
        $event就是浏览器创建的event对象, 默认传递给事件监听回调函数的就是它
     -->
    <button @click="test1">原生DOM事件监听</button>
    <button @click="test1($event)">原生DOM事件监听2</button>

    <br>
    <br>
    <Event1 @click.native="test2"/>

    <!-- 
      vue自定义事件
        绑定vue自定义事件监听
            只能在组件标签上绑定
            事件名是任意的, 可以与原生DOM事件名相同
        只有当执行$emit('自定义事件名', data)时分发自定义事件, 才会触发自定义事件监听函数调用
        $event: 就是分发自定义事件时指定的data数据
        $event可以是任意类型, 甚至可以没有
    -->
    <br>
    <br>
    <event2 @click="test3" @xxx="test4($event)"/>



<!-- 
1. 绑定事件监听
  事件名
  回调函数: 接收数据/事件对象, 处理事件
2. 分发事件
  事件名
  包含事件相关数据的对象(事件/event对象)
 -->

 <!-- 
   2个问题
  1. 区别原生事件与自定义事件
  2. 区别原生的$event与自定义的$event

  -->

  </div>
</template>

<script type="text/ecmascript-6">
  import Event1 from './Event1.vue'
  import Event2 from './Event2.vue'

  export default {
    name: 'EventTest',

    components: {
      Event1,
      Event2,
    },

    methods: {
     test1 (event) {
       alert(event.target.innerHTML)
     },

     test2 (event) {
       alert('----- ' + event.target.innerHTML)
     },

     test3 (data) {
       alert(data)
     },

     test4 (data) {
       alert('--' + data)
     }
    }
  }
</script>
