<template>
	<view>
		<text class="name">{{name}}</text>
		<text selectable>唱歌跳舞篮球</text>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				name: '唱歌跳舞篮球'
			}
		},
		methods: {

		}
	}
</script>

<style lang="scss">
	.name {
		color: #007AFF;
	}
</style>
