<template>
	<view>
		<view class="header">
			<image src="../../static/background.png" mode="widthFix" class="response"></image>
			<view class="header-img">
				<view class="cu-avatar xl round" style="background-image:url(http://node.pandaps.cn/static/img/head.jpg);">
					<view class="cu-tag badge cuIcon-male bg-blue"></view>
				</view>
				<h2>Cheney</h2>
			</view>
			<view class="header-bar">
				<view class="header-btn">
					<view class="number">
						1
					</view>
					<view class="text">
						文章
					</view>
				</view>
				<view class="header-btn">
					<view class="number">
						2
					</view>
					<view class="text">
						阅读
					</view>
				</view>
				<view class="header-btn">
					<view class="number">
						3
					</view>
					<view class="text">
						评论
					</view>
				</view>
			</view>
		</view>
		<scroll-view scroll-y class="page">
			<view class="cu-card article" v-for="(item,index) in dataSource" :key="index" @click="toDetil(item.url)">
				<view class="cu-item shadow" >
					<view class="title">
						<view class="text-cut">{{item.title}}</view>
					</view>
					<view class="content">
						<image :src="item.img" mode="aspectFill"></image>
						<view class="desc">
							<view class="text-content">{{item.url}}</view>
							<!-- <view>
								<view class="cu-tag bg-red light sm round">正义天使</view>
								<view class="cu-tag bg-green light sm round">史诗</view>
							</view> -->
						</view>
					</view>
				</view>
			</view>
		</scroll-view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				dataSource: [],
				TabCur: 0,
				scrollLeft: 0
			};
		},
		onLoad() {
			this.getData()
		},
		onShow() {
			//this.getData()
		},
		methods: {
			tabSelect(e) {
				this.TabCur = e.currentTarget.dataset.id;
				this.scrollLeft = (e.currentTarget.dataset.id - 1) * 60
			},
			getData() {
				uni.request({
					url: 'https://node.pandaps.cn/reptile/index',
					success: (res) => {
						console.log(res.data);
						this.dataSource = res.data;
					}
				});
			},
			toDetil(e) {
				console.log(e)
				uni.navigateTo({
					url: '/pages/detil/detil?id=' + e
				});
			}
		}
	}
</script>

<style>
	.header {
		width: 100vw;
		height: 30vh;
		position: fixed;
		top: 0vh;
		z-index: 99;
	}

	.header-img {
		width: 100vw;
		position: absolute;
		top: 10vh;
		text-align: center;
	}

	.header-bar {
		width: 92vw;
		height: 150rpx;
		border-radius: 7rpx;
		background: #FFFFFF;
		margin-left: 4vw;
		position: absolute;
		top: 25vh;
		box-shadow: 0 1px 10px 0 rgba(0, 0, 0, 0.1);
		display: flex;
		flex-direction: row;
		justify-content: space-around;

	}

	.header-btn {
		height: 150rpx;
		display: flex;
		flex-direction: column;
		text-align: center;
		align-items: center;
	}

	.number {
		height: 55rpx;
		padding-top: 10px;
		font-size: 38rpx;
		font-weight: 600;
	}

	.text {
		height: 55rpx;
		padding-top: 10px;
		font-size: 28rpx;
	}

	.page {
		width: 100vw;
		height: 70vh;
		margin-top: 35vh;
	}
</style>
