### vue 资讯详情
1. main.js 配置路由
    import newsinfo from './components/news/newsinfo.vue';
    {path:'/news/newsinfo/:id',component:newsinfo}
2. newslist.vue  <a></a>改为<router-link></router-link>
    <router-link v-bind="{to:'/news/newsinfo/'+item.id}"></router-link>
3. 页面传值
    data(){
			return {
				id:0
			}
		},
		created() {
			// 获取url传入的id参数赋值给data中的id属性，请求对应的内容详情
			// 注意  this.$route.params.id;  里的 id 要与 main.js里的{path:'/news/newsinfo/:id',component:newsinfo} :id 对应
			// 若为 ：id1 则为 this.$route.params.id1
			//页面传值
			this.id = this.$route.params.id;
		},

### vue 资讯详情 内容展示
1. 设计页面静态结构，没有使用任何UI控件,都是自己写的样式
2. 调用vue-resource 来请求服务器的数据
    2.1 地址： http://webhm.top:8899/api/getnew/:newid   
    2.2 方法：get()   写在 created()这个方法里
        this.$http.get(url);
3. 数据中有标签时利用 v-html 这个标签来解析详情数据，数据中没有标签时利用 v-html、v-text 这个标签来解析详情数据


### vue 公共功能提取 - api域名统一提取到kits下的common.js中 
1. 域名    http://webhm.top:8899
	开发环境域名
	测试环境域名
	正式环境域名
	域名会变，变的时候改动不好改，要改很多处，统一提取出来以后改变域名时很好改，只需配置文件即可
2. 在 src 下建 kits 文件夹 放公共的代码 名字可随意取
	common.js  负责管理当前系统中的所有公共的配置
	// common.js  负责管理当前系统中的所有公共的配置
	export default {
    	apidomain:' http://webhm.top:8899' //所有数据api的域名地址 ，域名发生改变时改这里就可以了
	}
3. 改动请求处的域名
	


