<template>
	<view class="container">
    <!-- 使用子组件，组件名和 import 变量名一致 -->
    <Userinfo 
      avatar="/static/image.png" 
      username="张三" 
    />
    <Userinfo 
      avatar="/static/logo.png" 
      username="李四" 
    />
    <Userinfo v-for="item in userInfo" v-bind="item"></Userinfo>
	</view>
</template>

<script setup>
// 正确路径：和实际文件结构完全一致（注意大小写和文件夹层级）
import Userinfo from '@/components/userinfo/userinfo.vue'
import { ref } from 'vue'

const userInfo = ref([
  {avatar: '/static/logo.png', username: '用户'},
  {avatar: '/static/image.png', username: '张三'},
  {avatar: '/static/logo.png', username: '李四'}
])
// 子组件的 props 定义
// 定义子组件接收的属性，包括 avatar 和 username
const props = defineProps({
  avatar: {
    type: String,
    default: '/static/logo.png'
  },
  username: {
    type: String,
    default: '用户'
  }
})
</script>

<style scoped lang="scss">
.container{
  padding: 20rpx;
}
</style>