<template>
    <div id='tmpl'>
        <!-- 轮播图 -->
        <mt-swipe :auto="1000">
            <!-- <mt-swipe-item>111111</mt-swipe-item>
                <mt-swipe-item>222222</mt-swipe-item>
                <mt-swipe-item>333333</mt-swipe-item> -->
            <mt-swipe-item v-for="item in list" :key="item.id">
                <img :src="item.list" alt="" />
            </mt-swipe-item>
        </mt-swipe>
    </div>
</template>
<script>
import { Toast } from 'mint-ui';
    export default {
        data() {
            return {
                list: []
            }
        },
        created() {
            // 当页面中的 data 和 methods 对象都创建完毕以后，就会自动调用created
            this.getimgs();
        },
        methods: {
            getimgs() {
                // 实现ajax 请求
                // 1.0 确定url
                var url ='http://webhm.top:8899/api/getlunbo';
                // 2.0用$http.get()
                this.$http.get(url).then(function(response){
                    var data = response.body;
                    // 错误处理 服务器返回的
                    if(data.status!=0){
                        Toast(data.message)
                        return
                    }
                    // 如果服务器返回的数据正常则赋值给list
                    this.list = data.message;

                })
            }
        }
    }
</script>
<style scoped>
    .mint-swipe {
        width: 100%;
        height: 300px;
    }
    .mint-swipe-item {
        width: 100%;
        height: 300px;
        background: red;
    }
    .mint-swipe-item img {
        width: 100%;
    }
</style>
