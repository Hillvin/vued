### vue 日期格式化   使用 momentjs   http://momentjs.cn/ 官网网址
1. 使用过滤器实现日期格式化功能
   使用私有过滤器Or全局过滤器   选择全局过滤器（该功能会在多个组件里使用）
2. 如何注册全局过滤器？
    Vue.filter('datefmt',function(input,fmtstring){})
    且在入口文件main.js里注册
3. 过滤器如何实现？  http://momentjs.cn/ 官网网址
    在这里使用momentjs类库来实现日期的格式化功能
    使用momentjs步骤
    1）安装：npm install moment --save  安装 moment 包
    2）导入 import moment from 'moment';
    3）写法：写在过滤器方法体中写入如下代码实现日期格式化
     Vue.filter('datefmt',function(input,fmtstring){
          return moment（input）.format（fmtstring）
     })
    4）在需要使用datefmt这个过滤器的组件中如何使用？
    {{ item.add_time | datafmt('YYYY-MM-DD HH:mm:ss') }}
    
       
