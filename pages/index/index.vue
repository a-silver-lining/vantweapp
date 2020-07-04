<template>
	<view class="content">
		<image class="logo" src="/static/logo.png"></image>
		<view class="text-area">
			<text class="title">{{title}}</text>
			<van-button type="danger" size="large" @click="onClick">危险按钮</van-button>
		</view>

		<van-tabbar :active="active" custom-class="tabbar" :safe-area-inset-bottom="false" active-color="#00EE00" @change="onChange">
			<!-- active当前选中标签的索引 -->
			<!-- home-o首页 search搜素查询  friends-o通讯录  setting-o设置 -->
			<van-tabbar-item icon="home-o">首页</van-tabbar-item>
			<van-tabbar-item icon="search">查询</van-tabbar-item>
			<van-tabbar-item icon="friends-o">通讯录</van-tabbar-item>
			<van-tabbar-item icon="setting-o">设置</van-tabbar-item>
			<van-tabbar-item info="3">
				<!-- :src是省略了v-bind，完整的写法 v-bind:src -->
				<image slot="icon" :src="icon.normal" class="imageicon" mode="widthFix" />
				<image slot="icon-active" :src="icon.active" class="imageicon" mode="widthFix" />
				自定义
			</van-tabbar-item>
		</van-tabbar>

	</view>
</template>

<script>
	var _self;
	export default {
		data() {
			return {
				title: 'Hello',
				active: 0,
				icon: {
					normal: '../../static/contactA.png',
					active: '../../static/contactB.png'
				}
			}
		},
		onLoad() {
			_self = this;
		},
		methods: {
			onChange: function(e) {
				_self.active = e.detail
				console.log(_self.active);
			},
			onClick: function() {
				console.log("危险按钮！！！");
			}
		},
	}
</script>

<style>
	.imageicon{
		width: 50rpx;
		height: 50rpx;
	}
	.content {
		display: flex;
		flex-direction: column;
		align-items: center;
		justify-content: center;
	}

	.logo {
		height: 200rpx;
		width: 200rpx;
		margin-top: 200rpx;
		margin-left: auto;
		margin-right: auto;
		margin-bottom: 50rpx;
	}

	.text-area {
		display: flex;
		justify-content: center;
	}

	.title {
		font-size: 36rpx;
		color: #8f8f94;
	}
</style>
