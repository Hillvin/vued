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
    export default {
        data(){
            return {
                list:[
                    {"id":1,"img":'https://timgsa.baidu.com/timg?image&quality=80&size=b9999_10000&sec=1537866851923&di=cfde4a24331343f4a1a28c84b435f87a&imgtype=0&src=http%3A%2F%2Fpic1.win4000.com%2Fwallpaper%2Fb%2F55597435bb036.jpg'},
                    {"id":2,"img":'https://timgsa.baidu.com/timg?image&quality=80&size=b9999_10000&sec=1537866888415&di=7e35fd6f9bd327cf123dc35df5488a81&imgtype=jpg&src=http%3A%2F%2Fimg4.imgtn.bdimg.com%2Fit%2Fu%3D2899142879%2C4043532548%26fm%3D214%26gp%3D0.jpg'},
                    {"id":3,"img":'https://timgsa.baidu.com/timg?image&quality=80&size=b9999_10000&sec=1537866852036&di=53cb60ce1a0ad6bdc05d0bf39f9dd7d5&imgtype=0&src=http%3A%2F%2Fimg5.duitang.com%2Fuploads%2Fitem%2F201407%2F05%2F20140705225720_KQkMH.jpeg'}
                ]
            }
        }
    }
</script>
<style scoped>
.mint-swipe{
    width:100%;
    height:300px;
}
.mint-swipe-item{
    width:100%;
    height:300px;
    background: red;
}
.mint-swipe-item img{
    width:100%;

}
</style>
