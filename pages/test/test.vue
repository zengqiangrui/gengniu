<template>
	<view>
		<view id="main" style="width: 300px;height:200px;"></view>
		<view id="main2" style="width: 400px;height:300px;"></view>
	</view>
</template>

<script>
	import echarts from "echarts/dist/echarts.js"

	export default {
		data() {
			return {}
		},
		mounted() {
			echarts.init(document.getElementById('main2')).setOption({
				xAxis: {
					type: 'category',
					data: ['Mon', 'Tue', 'Wed', 'Thu', 'Fri', 'Sat', 'Sun']
				},
				yAxis: {
					type: 'value'
				},
				series: [{
					data: [820, 932, 901, 934, 1290, 1330, 1320],
					type: 'line'
				}],
			});

			echarts.init(document.getElementById('main')).setOption({
				series: {
            name: '访问来源',
            type: 'pie',
            radius : '55%',
            center: ['50%', '60%'],
            data:[
                {value:2, name:'直接访问'},
                {value:98, name:'邮件营销'},
                
            ],
            itemStyle: {
                emphasis: {
                    shadowBlur: 10,
                    shadowOffsetX: 0,
                    shadowColor: 'rgba(0, 0, 0, 0.5)'
                }
            }
        }
			});
		},
		onLoad() {

		}
	}
</script>

<style>

</style>
