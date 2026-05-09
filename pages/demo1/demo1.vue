// 界面布局
<template>
	<!-- view展示标签。input是输入框，button是按键,text是文本标签 -->
	<!-- 
	class用于绑定样式，根据指令测试状态切换样式
	v-on:click="handleClick0" 用于绑定点击事件处理函数
	type="number" 用于输入框只接受数字输入
	@tap="onClick" 用于绑定点击事件处理函数，点击盒子时触发
	 -->
  <!-- 购物车选中与删除 -->
  <view class="cart">
    <view class="cart-item" v-for="item in gods" :key="item.id">
      <checkbox></checkbox>
      <text class="title">{{ item.name }}   {{ item.price }}</text>
      <text class="del" @click="delItem(item.id)">删除</text>
      <view class="price">¥{{ item.price }}</view>
      <view class="check" @click="itemChecked(item.id)">价格总数：{{ totalChecked }}</view>
      <view v-if="item.checked"><text>选中</text></view>
    </view>
  </view>

	<!-- 计数器 -->
	<view class="box" v-on:click="handleClick0">
		{{ i }}
	</view>
	<!-- 输入框 -->
	<view>
		<view>
      <view>
        <input class="input111" type="number" v-model="i.value" placeholder="输入计数器" />
      
        
        <text>确认</text>

        
      </view>
    </view>
		<text>当前计数器：{{ num }}</text>
		<button class="genbtn" v-on:click="changeI">更新</button>
	</view>
	<!-- 按键 -->
	<view>
		<button class="btn" v-on:click="handleClick1">按键</button>
	</view>
	<!-- 测试盒子 -->
	<view class="box" v-on:click="onClick" v-bind:style="{'background-color': color}">
		{{ isActive.value }}
	</view>
	<!-- 指令测试状态切换按钮 -->
	<view>
		<switch checked @change="onChange" />
		<button class="enable" type="primary" v-bind:loading="isLoading">普通点击</button>
	</view>
	<!-- 切换指令测试状态按钮 -->
	<view>
		<button class="btn" v-on:click="onClick">切换</button>
	</view>
  <!-- 篮球 -->
   <view v-for="item,index in 10" :key="index">模块{{ index + 1 }}</view>
   <view v-for="(item,index) in nba" :key="item.id">
    姓名： {{ item.name }}--爱好：{{ item.aihao }}--年龄：{{ item.year }} <br>
   </view>
</template>


// 逻辑处理
<script setup>
import { ref, onUnmounted,computed } from 'vue'
const appp = ref(null)
const i = ref(0);
const num = ref(0);
const isActive = ref(1);
const isLoading = ref(false);
let timer = null // 存储定时器，用于销毁
const color = ref('#8a3636');
const checked = ref([]);
const totalChecked = computed( () => {
  let total = 0;
  gods.value.forEach(item => {
    if(item.checked){
      total++;
    }
  })
  return total;
})

const gods = ref([
  {id:'1',name:"小米",price:19999,checked:false},
  {id:'2',name:"华为",price:29999,checked:false},
  {id:'3',name:"OPPO",price:39999,checked:false},
  {id:'4',name:"VIVO",price:49999,checked:false},
  {id:'5',name:"Realme",price:59999,checked:false},
]);


const nba = ref([
  {id:'1',name:'张三',aihao:'篮球',year:'23'},
  {id:'2',name:'李四',aihao:'足球',year:'18'},
  {id:'3',name:'王五',aihao:'跑步',year:'24'},
]);
// 定时1秒，增加计数器
timer = setInterval(()=>{
  i.value++;
  console.log(i.value);
}, 1000)

// 页面销毁时清除定时器（避免内存泄漏）
onUnmounted(() => {
  clearInterval(timer)
  timer = null // 清空定时器，避免内存泄漏
})
// 输入框内容改变时，更新计数器
function changeI(){
  i.value = Number(i.value);
  num.value = Number(i.value);
}
// 切换指令测试状态
function onChange(e){
  console.log(e.detail.value);
  isLoading.value = e.detail.value;
}
// 点击盒子时，切换指令测试状态
function onClick(){
  isActive.value = isActive.value++;
  console.log(Math.random());
  color.value = '#'+Math.random().toString(16).substring(2,8);
  console.log(color.value);
}

// 删除商品
function delItem(id){
  console.log(id);
  gods.value = gods.value.filter(item => item.id !== id);
}
function itemChecked(id){
  console.log(id);
  gods.value.forEach(item => {
    if(item.id === id){
      item.checked = !item.checked;
    }
  })
}
// 按钮点击事件处理函数
const handleClick0 = () => {
  console.log('按钮被点击了'),
  uni.showToast({
    title: '按钮被点击了',
    icon: 'none'
  })
}
const handleClick1 = () => {
  console.log('按键被点击了'),
  uni.showToast({
    title: '按键被点击了',
    icon: 'none'
  })
}
</script>



// 测试盒子样式
<style lang="scss">
/* 
font-size是文本字体大小
color是文本颜色
text-align是文本对齐方式，用于水平居中显示
line-height是行高，用于垂直居中显示
*/
.box {
  width: 200px;
  height: 200px;
  background-color: #8a3636;
  font-size: 20px;
  color: #fff;
  text-align: center;
  line-height: 200px;
}
.animate {
  animation: move 1s linear infinite;
}
.btn {
  width: 100px;
  height: 50px;
  background-color: #fff;
  color: #8a3636;
  border: 1px solid #8a3636;
}
.btn:hover {
  background-color: #8a3636;
  color: #fff;
}
.genbtn {
  width: 100px;
  height: 50px;
  background-color: #fff;
  color: #8a3636;
  border: 1px solid #8a3636;
}
.genbtn:hover {
  background-color: #8a3636;
  color: #fff;
}
.enable {
  width: 100%;
  height: 50px;
  background-color: #fff;
  color: #8a3636;
  border: 1px solid #8a3636;
}
.enable:hover {
  background-color: #8a3636;
  color: #fff;
}
.cart {
  margin-top: 20px;
}
.cart-item {
  display: flex;
  align-items: center;
}
.title {
  flex: 1;
}
.del {
  color: #f80404;
}
.input111 {
  width: 50%;
  height: 30px;
  margin-right: 10px;
  margin-bottom: 10px;
  border: 1px solid #8a3636;
  padding-left: 10px;
  font-size: 16px;
}
</style>
