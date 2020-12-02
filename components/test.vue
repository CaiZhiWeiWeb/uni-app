<template>
	<view>
		这是test组件{{title}}
		<button type="default" @click="sendPar">触发时间</button>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				part:'ccc'
			}
		},
		props:['title'],
		beforeCreate() {
			console.log('beforeCreate')
		},
		created(){
			console.log('created')
		},
		beforeMount() {
			console.log('beforeMount')
		},
		mounted() {
			console.log('mounted')
		},
		beforeUpdate() {
			console.log('beforeUpdate')
		},
		updated() {
			console.log('updated')
		},
		beforeDestroy() {
			console.log('beforeDestroy')
		},
		destroyed() {
			console.log('destroyed')
		},
		methods: {
			sendPar(){
				this.$emit('update',this.part)
			}
		}
	}
</script>

<style>

</style>
