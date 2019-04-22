<template>
    <div class="search">
        <div class="searchTop">
            <span>北京</span>
            <p class="putone"><input type="text" placeholder="新浪" @change="goSearch"></p>
        </div>
        <div class="center">
            <scroll-view scroll-y style="width:100%;height:100%">
                <ul class="searchList">
                    <li class="everyList">
                        <img src="/static/images/location.svg" alt="">
                        <div class="title">
                            <h3>腾讯科技(北京)有限公司</h3>
                            <span>北京市海定区海淀区海淀大街38号银科大厦2-17层</span>
                        </div>
                    </li> 
                </ul>
            </scroll-view>
        </div>
    </div>
</template>

<script>
// 引入SDK核心类
// import QQMapWX from '../../libs/qqmap-wx-jssdk'
let qqmapsdk;
export default {
    data(){
        return{
            addressData:[],
            key:'',
            QQMapWX:'/libs/qqmap-wx-jssdk'
        }
    },  
    created(){
        // 实例化API核心类
        qqmapsdk = new QQMapWX({
            key: 'MWOBZ-T4ZLD-TP343-H3JYT-OXTES-5IBR3'
        });
    },
    methods:{
        goSearch(e){
            // console.log(e.target.value)
            let val=e.target.value
            wx.request({
                url:"https://apis.map.qq.com/ws/place/v1/suggestion/?region=%E5%8C%97%E4%BA%AC&keyword=%E6%8B%9B%E8%81%98web&key=key"
            })
        }
    },
    onShow: function () {
        // 调用接口
        qqmapsdk.search({
            keyword: '招聘',
            success: function (res) {
                console.log(res);
            },
            fail: function (res) {
                console.log(res);
            },
            complete: function (res) {
                console.log(res);
            }
        })
    }
}
</script>

<style>
.search{
    width:100%;
    height: 100%;
    display: flex;
    flex-direction: column;
}
.searchTop{
    width: 100%;
    height: 10%;
    border-top: 1px solid #ccc;
    border-bottom: 1px solid #ccc;
    display: flex;
    align-items: center;
}
.searchTop span{
    width: 20%;
    text-align: center;
    border-right: 1px solid #ccc;
}
.putone{
    margin-left: 10px;
}
.searchList{
    width:100%;
    height:auto;
}
.center{
    width: 100%;
    height: 90%;
}
.everyList{
    width: 100%;
    height: 90px;
    border-bottom: 1px solid #ccc;
    padding: 0 10px;
    box-sizing: border-box;
    display: flex;
    align-items: center;
}
.everyList img{
    width: 25px;
    height: 25px;
    margin: 0 10px;
}
.title{
    display: flex;
    flex-direction: column;
}
.title h3{
    color: #000;
}
.title span{
    font-size: 14px;
    color: #999;
}
</style>
