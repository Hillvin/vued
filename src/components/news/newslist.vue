<template>
	<div id='tmpl'>
		<ul class="mui-table-view">
			<li class="mui-table-view-cell mui-media" v-for="item in list">
				<a href="javascript:;">
					<img class="mui-media-object mui-pull-left" :src="item.img_url">
					<div class="mui-media-body">
						{{item.title}}
						<p class='mui-ellipsis' v-text="item.zhaiyao"></p>
					</div>
					<div class="ft">
						<span>发布时间：{{item.add_time | datefmt('YYYY-MM-DD HH:mm:ss') }}</span>
						<span class="click">点击数：{{item.click}}</span>
					</div>
				</a>
			</li>
			
		</ul>
	</div>
</template>
<script>
import {Toast} from 'mint-ui';

	export default {
		data() {
			return {
				list: [
					
				]
			}
		},
		created() {
			this.getnewslist();
		},
		methods: {
			getnewslist() {
				// 写死的
				this.list = [
					{
						"id":'0001',
						"title":'aaaaa',
						"add_time":'2019-06-25T11:15:25+08:00',
						"zhaiyao":'AAAAA',
						"click":'1',
						"img_url":'http://00000000000000',
					},
					{
						"id":'0001',
						"title":'aaaaa',
						"add_time":'2019-06-25T11:15:25+08:00',
						"zhaiyao":'AAAAA',
						"click":'1',
						"img_url":'http://00000000000000',
					},
					{
						"id":'0001',
						"title":'aaaaa',
						"add_time":'2019-06-25T11:15:25+08:00',
						"zhaiyao":'AAAAA',
						"click":'1',
						"img_url":'http://00000000000000',
					}
				]

				// 动态获取
				// var url = 'http://webhm.top:8899/api/getnewslist';
				// this.$http.get(url).then(function(res){
				// 	var body = res.body;
				// 	// 错误信息处理
				// 	if(body.status != 0){
				// 		Toast(body.message);
				// 		return;
				// 	}
				// 	this.list = body.message;
				// })


			}
		}
	}
</script>
<style scoped>
.mui-table-view img{
	width:80px;
	height: 80px;
}
.mui-table-view .mui-media-object{
	line-height: 80px;
    max-width: 80px;
}
.ft{
	margin-top: 1.5em;
	font-size: 14px;
	color: #0094ff;
}
.click{
	margin-left: 0px;
}
</style>
