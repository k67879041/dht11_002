<template>
	<view class="userinfo">
		<!-- 保留 mode="aspectFill" 适配圆形头像 -->
		<image :src="avatar" mode="aspectFill" class="avatar"></image>
		<view class="username">{{ username }}</view>
	</view>
</template>

<script setup>
import { computed } from 'vue';
import { ref } from 'vue';

// 接收父组件传递的头像、用户名
const props = defineProps({
  avatar: {
    type: String,
    required: true
  },
  username: {
    type: String,
    required: true
  }
})
// 如果没有传值，就显示默认值“用户”，图片默认显示“static/logo.png”
const avatar = computed(() => props.avatar || '/static/logo.png');
const username = computed(() => props.username || '用户');
</script>

<style scoped lang="scss">
.userinfo{
  width: 100%;
  height: 400rpx; /* 改用 rpx 适配移动端 */
  background: #ccc;
  display: flex;
  align-items: center;
  justify-content: center;
  flex-direction: column;
  
  .avatar{
    width: 200rpx;
    height: 200rpx;
    border-radius: 50%;
    border: 6rpx solid #fff;
    /* ✅ 必须加！让圆形裁剪生效 */
    overflow: hidden;
    object-fit: cover;
  }

  .username{
    padding: 20rpx 0;
    font-size: 32rpx;
    text-align: center;
  }
}
</style>