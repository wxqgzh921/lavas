<template>
	<div class="getdata">
		<h3>使用axios获取到数据(看控制台)</h3>
		<p>{{a}},{{b}}</p>
	</div>
</template>
<script>
import axios from 'axios';
	export default{
		name:'getData',
		data(){
			return {
				a:'',
				b:''
			}
		},
		async asyncData(){
			let result = await axios(`https://query.yahooapis.com/v1/public/yql?q=select%20item.condition%20from%20weather.forecast%20where%20woeid%20%3D%202151849&format=json&env=store%3A%2F%2Fdatatables.org%2Falltableswithkeys`);
			let condition = result.data.query.results.channel.item.condition;
			console.log(`Weather of Shanghai:${condition.text},${condition.temp}°F`);
			console.log(this.a)
		}
	}
</script>