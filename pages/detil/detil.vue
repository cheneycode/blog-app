<template>
	<view>
		<web-view :webview-styles="webviewStyles" :src="urls"></web-view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				webviewStyles: {
					progress: {
						color: '#FF3333'
					}
				},
				urls: ''
			}
		},
		onLoad(params) {
			this.urls = 'https://node.pandaps.cn/reptile/' + params.id
			console.log(this.urls)
		},
		methods: {
			// getData() {
			// 	uni.request({
			// 		url: 'https://node.pandaps.cn/reptile/story/9721181',
			// 		success: (res) => {
			// 			console.log(res.data);
			// 			this.dataSource = res.data;
			// 		}
			// 	});
			// }
		}
	}
</script>

<style>

</style>
