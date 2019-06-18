<template>
	<view class="main">
		<view class="header">
			
		</view>
	</view>
</template>

<script>

	var data = {
		
	}
	
	export default {
		props: ["table"],
		data: function() {
			return data
		},
		mounted() {
			console.log("thistable",this.table)
			this.table.tableshow()
		},
		methods: {
			
		}
	}
	

</script>

<style>
</style>
