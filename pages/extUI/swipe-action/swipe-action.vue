<template>
	<view>
		<uni-section title="基本用法" type="line"></uni-section>
		<uni-swipe-action :options="options2" @click="bindClick">
			<text class="cont">SwipeAction 基础使用场景</text>
		</uni-swipe-action>
		<uni-section title="禁止滑动" type="line"></uni-section>
		<uni-swipe-action :disabled="true">
			<text class="cont">SwipeAction 禁止滑动展示</text>
		</uni-swipe-action>
		<uni-section title="使用变量控制开关" type="line"></uni-section>
		<view class="example-body">
			<view class="button" @click="setOpened"><text class="button-text">当前状态：{{ isOpened ? '开' : '关' }}</text></view>
		</view>
		<uni-swipe-action :options="options2" :show="isOpened" :auto-close="false" @change="change">
			<text class="cont">使用变量控制SwipeAction的开启状态</text>
		</uni-swipe-action>
		<uni-section title="与 List 组件一起使用" type="line"></uni-section>
		<uni-list>
			<uni-swipe-action :options="options1">
				<uni-list-item :show-arrow="false" title="item1" />
			</uni-swipe-action>
			<uni-swipe-action :options="options2">
				<uni-list-item :show-arrow="false" title="item2" />
			</uni-swipe-action>
			<uni-swipe-action :options="options3">
				<uni-list-item :show-arrow="false" title="item3" />
			</uni-swipe-action>
		</uni-list>
	</view>
</template>

<script>
	import uniSection from '@/components/uni-section/uni-section.vue'
	import uniSwipeAction from '@/components/uni-swipe-action/uni-swipe-action.vue'
	import uniList from '@/components/uni-list/uni-list.vue'
	import uniListItem from '@/components/uni-list-item/uni-list-item.vue'
	export default {
		components: {
			uniSection,
			uniSwipeAction,
			uniList,
			uniListItem
		},
		data() {
			return {
				isOpened: false,
				options1: [{
					text: '取消置顶'
				}],
				options2: [{
					text: '取消',
					style: {
						backgroundColor: '#007aff'
					}
				}, {
					text: '确认',
					style: {
						backgroundColor: '#dd524d'
					}
				}],
				options3: [{
					text: '置顶'
				}, {
					text: '标记为已读',
					style: {
						backgroundColor: 'rgb(254,156,1)'
					}
				}, {
					text: '删除',
					style: {
						backgroundColor: 'rgb(255,58,49)'
					}
				}]
			}
		},
		onReady() {
			this.$nextTick(() => {
				this.isOpened = true
			})
		},
		methods: {
			bindClick(e) {
				console.log(e)
				uni.showToast({
					title: `点击了${e.content.text}按钮`,
					icon: 'none'
				})
			},
			setOpened() {
				this.isOpened = !this.isOpened
			},
			change(e) {
				this.isOpened = e
			}
		}
	}
</script>

<style>
	/* 头条小程序组件内不能引入字体 */
	/* #ifdef MP-TOUTIAO */
	@font-face {
		font-family: uniicons;
		font-weight: normal;
		font-style: normal;
		src: url('~@/static/uni.ttf') format('truetype');
	}

	/* #endif */

	/* #ifndef APP-NVUE */
	page {
		display: flex;
		flex-direction: column;
		box-sizing: border-box;
		background-color: #efeff4;
		min-height: 100%;
		height: auto;
	}

	view {
		font-size: 28rpx;
		line-height: inherit;
	}

	.example {
		padding: 0 30rpx 30rpx;
	}

	.example-info {
		padding: 30rpx;
		color: #3b4144;
		background: #ffffff;
	}

	.example-body {
		flex-direction: row;
		flex-wrap: wrap;
		justify-content: center;
		padding: 0;
		font-size: 14rpx;
		background-color: #ffffff;
	}

	/* #endif */
	.example {
		padding: 0 30rpx;
	}

	.example-info {
		/* #ifndef APP-NVUE */
		display: block;
		/* #endif */
		padding: 30rpx;
		color: #3b4144;
		background-color: #ffffff;
		font-size: 30rpx;
	}

	.example-info-text {
		font-size: 28rpx;
		line-height: 36rpx;
	}


	.example-body {
		flex-direction: column;
		padding: 30rpx;
		background-color: #ffffff;
	}

	.word-btn-white {
		font-size: 18px;
		color: #FFFFFF;
	}

	.word-btn {
		/* #ifndef APP-NVUE */
		display: flex;
		/* #endif */
		flex-direction: row;
		align-items: center;
		justify-content: center;
		border-radius: 6px;
		height: 48px;
		margin: 15px;
		background-color: #007AFF;
	}

	.word-btn--hover {
		background-color: #4ca2ff;
	}


	.cont {
		height: 45px;
		line-height: 45px;
		padding: 0 15px;
		position: relative;
		background-color: #fff;
		font-size: 15px;
	}

	.example-body {
		/* #ifndef APP-NUVE */
		display: flex;
		/* #endif */
		flex-direction: row;
		justify-content: center;
		padding: 10px 0;
	}

	.button {
		border-color: #e5e5e5;
		border-style: solid;
		border-width: 1px;
		padding: 4px 8px;
		border-radius: 4px;
	}

	.button-text {
		font-size: 15px;
	}
</style>