<template>
  <view class="dht11-002">
    <!-- 用 view 包裹 image，view 负责裁剪，image 只负责显示 -->
    <view class="avatar-wrap">
      <image :src="avatar" mode="aspectFill"></image>
    </view>
    <view class="username">{{ username }}</view>
  </view>
</template>

<style scoped lang="scss">
.dht11-002 {
  width: 100%;
  height: 400rpx;
  background: #ccc;
  display: flex;
  align-items: center;
  justify-content: center;
  flex-direction: column;

  /* 外层 view 做圆形，兼容性拉满 */
  .avatar-wrap {
    width: 200rpx;
    height: 200rpx;
    border-radius: 50%;
    border: 6rpx solid #fff;
    overflow: hidden;
    image {
      width: 100%;
      height: 100%;
      object-fit: cover;
    }
  }

  .username {
    padding: 20rpx 0;
    font-size: 32rpx;
    text-align: center;
  }
}
</style>