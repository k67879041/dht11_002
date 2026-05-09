<template>
	<view class="container">
    <!-- 使用子组件，组件名和 import 变量名一致 -->
    <Userinfo 
      avatar="/static/image.png" 
      :username="name" 
    />
    <view class="line">我的发贴</view>
    <view class="line">我的关注</view>
    <view class="line">我的收藏</view>
    <view class="line">我的评论</view>
    <view class="line">我的点赞</view>
    <view class="line">我的回复</view>
    <view class="line">我的抽奖</view>
    <view class="line">设置</view>
    <text class="title">我的</text>
	</view>
</template>

<script setup>
// 正确路径：和实际文件结构完全一致（注意大小写和文件夹层级）
import Userinfo from '@/components/userinfo/userinfo.vue'
import { ref } from 'vue';
const name = ref('易平安');
const xianshiid = ref(
  {id:1,name:'我的发贴'},
  {id:2,name:'我的关注'},
  {id:3,name:'我的收藏'},
  {id:4,name:'我的评论'},
  {id:5,name:'我的点赞'},
  {id:6,name:'我的回复'},
  {id:7,name:'我的抽奖'},
  {id:8,name:'设置'}
)
</script>

<style scoped lang="scss">
.container{
  padding: 20rpx;
}
// “我的” 一般位于页面低部右侧
.title{
  font-size: 32rpx;
  text-align: center;
  margin-top: 20rpx;
  color: #333;
  font-weight: bold;
  border-bottom: 2rpx solid #333;
  padding-bottom: 20rpx;
  margin-bottom: 20rpx;
  display: block;
}
.line{
  font-size: 32rpx;
  text-align: center;
  margin-top: 20rpx;
  color: #333;
  font-weight: bold;
  border-bottom: 2rpx solid #333;
  padding-bottom: 20rpx;
  margin-bottom: 20rpx;
  display: block;
}

</style>