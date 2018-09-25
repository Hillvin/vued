### vued 
ajax 获取图片 轮播图
使用 mint-ui 里的 <mt-swipe></mt-swipe>组件 http://mint-ui.github.io/docs/#/zh-cn2/swipe
1.  <mt-swipe :auto="4000">
        <mt-swipe-item>1</mt-swipe-item>
        <mt-swipe-item>2</mt-swipe-item>
        <mt-swipe-item>3</mt-swipe-item>
    </mt-swipe>
2. vue-resource
   npm i vue-resource --save
3. //7.0 将vue-resource 在vue中绑定，自动在vue对象实例上注入一个$http对象就可以使用ajax方法了
    import vueResource from 'vue-resource';
    Vue.use(vueResource);
4. 