### vuec
1. 顶部用mint-ui即可
2. 中间用 <router-view>占位即可
3. 底部用MUI即可
    注意：
    * 底部切换高亮显示可以用 
        利用https://router.vuejs.org/zh/installation.html网站里的router-link（API文档里） 里的active-class有默认值可以通过路由的构造选项 linkActiveClass 来全局配置
        即 main.js 里的
            var router1 = new vueRouter({
                linkActiveClass:'mui-active',
	            routes:[
		                    {path:'/login',component:login}, 
		                    {path:'/register',component:register}
	                    ]
	        });
4.  App.vue
    <router-link class="mui-tab-item" to="/home"></router-link>
    <router-link class="mui-tab-item" to="/shopcar"></router-link>
    main.js
    import home from './components/Home.vue';
    import shopcar from './components/shopcar/car.vue';
    var router1 = new vueRouter({
	    routes:[
		    {path:'/home',component:home}, 
		    {path:'/shopcar',component:shopcar}
	    ]
	});
    components下建Home.vue
    components下建shopcar文件夹里面建car.vue
5. 注意 每个组件 template里的div会被header挡住一部分；每个div上加个id='tmpl' 
    #tpml{margin-top:45px;margin-bottom: 50px;}写在site.css里