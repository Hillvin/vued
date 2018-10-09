<template>
	<div id='tmpl'>
		
		<!-- 写死 -->
		<!-- <div class="title">
			<h4>标题</h4>
			<p>2020-1-1 1 次浏览</p>
		</div>
		<div id="content">
			咋啊啊啊啊啊啊啊啊啊啊啊啊啊啊啊啊啊啊啊啊啊啊啊啊啊啊啊
		</div> -->

		<!-- 从数据中获取 写死 -->
		<!-- <div class="title">
			<h4 v-text="info.title">标题</h4>
			<p>{{info.add_time | datefmt('YYYY-MM-DD') }} {{ info.click }}次浏览</p>
		</div>
		<div id="content" v-html="info.content">
			咋啊啊啊啊啊啊啊啊啊啊啊啊啊啊啊啊啊啊啊啊啊啊啊啊啊啊啊
		</div> -->

		<!-- 动态获取 -->
		<div class="title">
			<h4 v-text="info.title">标题</h4>
			<p>{{info.add_time | datefmt('YYYY-MM-DD') }} {{ info.click }}次浏览</p>
		</div>
		<div id="content" v-html="info.content">
			咋啊啊啊啊啊啊啊啊啊啊啊啊啊啊啊啊啊啊啊啊啊啊啊啊啊啊啊
		</div>

	</div>
</template>
<script>
	export default {
		data() {
			return {
				id: 0,//传入的id值
				info:{
					// 'id':12,
					// 'title':"aaaaaaaaaaaaaaaaa",
					// 'click':1,
					// 'add_time':"2019-06-25T11:15:25+08:00",
					// 'content':'AAAAAAAAAAAAAAAAAAAAAAAAAAaaaaaaaaaaaaaaaaaaaaaaaaaa'
				}
			}
		},
		created() {
			// 获取url传入的id参数赋值给data中的id属性，请求对应的内容详情
			// 注意  this.$route.params.id;  里的 id 要与 main.js里的{path:'/news/newsinfo/:id',component:newsinfo} :id 对应
			// 若为 ：id1 则为 this.$route.params.id1
			// 1.0 页面传值  获取对应消息的id
			this.id = this.$route.params.id;
			// 2.0 请求服务器获取到这个 id 对应的详情数据对象
			this.getinfo();
		},
		methods:{
			getinfo(){
				// 1.0 定义 url
				var url = 'http://webhm.top:8899/api/getnew/'+this.id;
				// 2.0 
				this.$http.get(url).then(function(res){
					var body = res.body;
					if(body.status != 0 ){
						alert("body.message");
						return;
					}
					//3.0 赋值给data里的info
					this.info = body.message[0]
				})

			}
		}
	}
</script>
<style scoped>
	.title h4 {
		color: #0094ff;
	}
	.title p {
		color: rgba(0, 0, 0, 0.5);
	}
	.title,#content{
		padding: 5px;
	}
</style>
