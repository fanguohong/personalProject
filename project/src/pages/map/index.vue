<template>
    <div class="mapBox">
        <map class="maps"
        id="myMap"
        longitude="116.300278"
        latitude="40.040848"
        scale="18"
        :markers="markers"
        show-location
        >
        
        </map>
        <div class="imgs">
            <img src="../../../static/images/location.png" class="cap" @click="goPosition"/>
            <img src="../../../static/images/my.png" @click="personCenter"/>
        </div>
        <div class="last">
            <span @click="addInter">添加面试</span>
        </div>
    </div>
</template>

<script>

export default {
    data(){
        return{
            markers:[{
                iconPath:'/static/images/loc.png',
                id:0,
                latitude:40.040848,
                longitude:116.300278,
                width:50,
                height:50
            }]
        }
    },
    methods:{
        goPosition(e){
            let mpCtx=wx.createMapContext("myMap");
            console.log('1',mpCtx)
            mpCtx.moveToLocation()
        },
        personCenter(){
            wx.navigateTo({
                url: '/pages/personCenter/main'
            });
        },
        addInter(){
            wx.navigateTo({
                url:'/pages/interview/main'
            })
        }
    },
    created(){
        // console.log('地图定位！')
        // var that = this
        // wx.getLocation({
        //     type: 'gcj02', //返回可以用于wx.openLocation的经纬度
        //     success: function (res) {
        //         var latitude = res.latitude; 
        //         var longitude = res.longitude; 
        //         wx.openLocation({
        //             latitude:latitude,
        //             longitude:longitude,
        //             scale:1
        //         })
        //     }
        // });
       
    }
    
}
</script>

<style>
.mapBox{
    width: 100%;
    height: 100%;
    position: relative;
}
.maps{
    width: 100%;
    height: 100%;
}
.imgs{
    width: 100%;
    height: 50px;
    padding: 0 10px;
    box-sizing: border-box;
    position: absolute;
    left: 0;
    bottom: 10%;
    display: flex;
    justify-content: space-between;
    align-items: center;
}
.imgs img{
    width: 40px;
    height: 40px;
}
.last{
    width: 90%;
    height: 40px;
    background: #000;
    color: #fff;
    text-align: center;
    line-height: 40px;
    position: absolute;
    left: 5%;
    bottom: 1%;
}
.image-cnt {
  display: flex;
  align-items: center;
  justify-content: center;
  margin-top: 50px;
}
.cover-image{
    width: 30px;
    height:30px;
}
</style>
