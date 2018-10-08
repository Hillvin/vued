<template>
    <div id='tmpl'>
        <!-- mint-ui swipe 轮播图 -->
        <mt-swipe :auto="1000">
            <!-- <mt-swipe-item>111111</mt-swipe-item>
                            <mt-swipe-item>222222</mt-swipe-item>
                            <mt-swipe-item>333333</mt-swipe-item> -->
            <mt-swipe-item v-for="item in list" :key="item.id">
                <img :src="item.list" alt="" />
            </mt-swipe-item>
        </mt-swipe>
        <!-- MUI 九宫格 -->
        <div class="mui-content">
            <ul class="mui-table-view mui-grid-view mui-grid-9">
                <li class="mui-table-view-cell mui-media mui-col-xs-4 mui-col-sm-3">
                    <router-link to="/news/newslist">
                        <span class="mui-icon mui-icon-home"></span>
                        <div class="mui-media-body">新闻资讯</div>
                    </router-link>
                </li>
                <li class="mui-table-view-cell mui-media mui-col-xs-4 mui-col-sm-3">
                    <router-link to="/photo/photolist">
                        <span class="mui-icon mui-icon-email"></span>
                        <div class="mui-media-body">图片分享</div>
                    </router-link>
                </li>
                <li class="mui-table-view-cell mui-media mui-col-xs-4 mui-col-sm-3">
                    <router-link to="/goods/goodslist">
                        <span class="mui-icon mui-icon-chatbubble"></span>
                        <div class="mui-media-body">商品购买</div>
                    </router-link>
                </li>
                <li class="mui-table-view-cell mui-media mui-col-xs-4 mui-col-sm-3">
                    <router-link to="/feedback">
                        <span class="mui-icon mui-icon-location"></span>
                        <div class="mui-media-body">留言反馈</div>
                    </router-link>
                </li>
                <li class="mui-table-view-cell mui-media mui-col-xs-4 mui-col-sm-3">
                    <router-link to="/vide">
                        <span class="mui-icon mui-icon-search"></span>
                        <div class="mui-media-body">视频专区</div>
                    </router-link>
                </li>
                <li class="mui-table-view-cell mui-media mui-col-xs-4 mui-col-sm-3">
                    <router-link to="/callme">
                        <span class="mui-icon mui-icon-phone"></span>
                        <div class="mui-media-body">联系我们</div>
                    </router-link>
                </li>
            </ul>
        </div>
    </div>
</template>
<script>
    import {
        Toast
    } from 'mint-ui';
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
            // 轮播图
            getimgs() {
                // 实现ajax 请求
                // 1.0 确定url
                var url = 'http://webhm.top:8899/api/getlunbo';
                // 2.0用$http.get()
                this.$http.get(url).then(function(response) {
                    var data = response.body;
                    // 错误处理 服务器返回的
                    if (data.status != 0) {
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
    .mui-content {
        background-color: #fff;
    }
    .mui-content ul {
        background-color: #fff;
    }
    .mui-grid-view.mui-grid-9 .mui-table-view-cell {
        border-right: 0px solid #eee;
        border-bottom: 0px solid #eee;
    }
    .mui-grid-view.mui-grid-9{
        border-top: 0px solid #eee;
        border-left: 0px solid #eee;
    }
    .mint-swipe-item img {
        width: 100%;
    }
    .mui-icon-home:before,
    .mui-icon-email:before,
    .mui-icon-chatbubble:before,
    .mui-icon-location:before,
    .mui-icon-search:before,
    .mui-icon-phone:before {
        content: '';
        display: inline-block;
        width: 50px;
        height: 50px;
        background-repeat: round;
    }
    .mui-icon-home:before {
        background-image: url(../../statics/imgs/1.png);
    }
    .mui-icon-email:before {
        background-image: url(../../statics/imgs/2.png);
    }
    .mui-icon-chatbubble:before {
        background-image: url(../../statics/imgs/3.png);
    }
    .mui-icon-location:before {
        background-image: url(../../statics/imgs/4.png);
    }
    .mui-icon-search:before {
        background-image: url(../../statics/imgs/5.png);
    }
    .mui-icon-phone:before {
        background-image: url(../../statics/imgs/6.png);
    }
</style>
