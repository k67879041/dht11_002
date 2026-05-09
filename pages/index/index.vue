
<template>
  <!-- 页面根容器 -->
  <view class="content" id="app">
    <!-- 欢迎文本 -->
    <text>你好</text>   
    
    <!-- 标题 -->
    <view class="title">OneNET 物联网控制器</view>
    <view><navigator url="/pages/demo1/demo1">跳转测试demo1</navigator></view>
    <!-- 测试文本和嵌套视图 -->
    <view>sdasdsa<view>ssss</view>dsadsff</view>
    
    <!-- 图片轮播组件 -->
    <!-- 使用 v-bind:src 或简写 :src 绑定图片路径 -->
    <!-- mode="aspectFill" 保持图片比例填充 -->
    <image v-bind:src="picur" mode="aspectFill"></image>
    
    <!-- 按钮组件 -->
    <!-- 使用 @click 或 v-on:click 绑定点击事件 -->
    <button @click="handleClick" type="primary" class="load">按键</button>
    
    <!-- 静态图片展示 -->
    <image v-bind:src="arrs[1]" mode="widthFix">第一张</image>
    <image v-bind:src="arrs[3]" mode="widthFix">第二张</image>
  </view>
  
  <!-- 测试视图 -->
  <view class="box">指令测试</view>
  <view class="box" v-bind:class="{'active': isActive}">点击测试</view>
  <view class="box" v-bind:class="isActive ? 'active':''" v-bind:style="{'font-size': isActive?'20px':'16px'}">三元运算符</view>
  <view class="box" v-bind:style="{'font-size': size+'px'}">内联样式</view>
</template>
// font-size是文本字体大小,根据指令测试状态切换
<script setup>
// 导入 Vue 3 的 ref 函数用于创建响应式数据
import { ref } from 'vue'

// 图片路径数组
// 使用 ref 创建响应式数组，存储图片路径
const arrs = ref([
  "/static/logo.png",
  "/static/微信图片_20231001123629.jpg",
  "/static/微信图片_20231002191649.jpg",
  "/static/微信图片_20231002191706.jpg"
]);

// 指令测试状态
// 使用 ref 创建响应式变量，初始值为 false
const isActive = ref(true)
// 文本字体大小
// 使用 ref 创建响应式变量，初始值为 20px
const size = ref(20)

// 当前显示的图片路径
// 使用 ref 创建响应式变量，初始值为第一张图片
const picur = ref('/static/logo.png')

// 图片索引计数器
let i = 0;

// 定时1秒，切换显示图片
// setInterval 函数用于定时执行图片切换
// i%4 确保索引在 0-3 之间循环
setInterval(()=>{
  i++;
  // 访问 ref 变量的值需要使用 .value
  picur.value = arrs.value[i%4];
  isActive.value = !isActive.value;
  size.value = size.value +10;
}, 1000)

// 按钮点击事件处理函数
const handleClick = () => {
  console.log('按钮被点击了'),
  uni.showToast({
    title: '按钮被点击了',
    icon: 'none'
  })
}
</script>

<style lang="scss">
/* 测试盒子样式 
 * 指令测试状态时，背景颜色为黄色
 * 非指令测试状态时，背景颜色为白色
 * 指令测试状态时，文本颜色为红色
 * 非指令测试状态时，文本颜色为黑色
 * 指令测试状态时，文本为"指令测试"
 * 非指令测试状态时，文本为"点击测试"
 * 指令测试状态时，文本字体大小为20px
 * 非指令测试状态时，文本字体大小为16px
 */
.box {
  width: 200px;
  height: 200px;
  background-color: #8a3636;
  border: 1px solid #201f1f;
  margin-top: 20px;
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 20px;
}

/* 按钮样式 */
.load {
  width: 100px;
  height: 50px;
  background-color: cornflowerblue;
  margin: 20px 0;
}

/* 标题样式 */
.title {
  font-size: 20px;
  font-weight: bold;
  margin: 10px 0;
}

/* 内容容器样式 */
.content {
  padding: 20px;
}

/* 指令测试状态时的样式 */
.active {
  width: 200px;
  height: 200px;
  background-color: yellow;
  color: red;
  font-size: 20px;
}
</style>