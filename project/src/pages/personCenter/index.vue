<template>
    <div class="ownBox">
       <div class="own">
           <p><img src="/static/images/my.png"/></p>
        </div> 
        <div class="listOwn">
            <div class="myinterview">
                <p class="one">
                    <icon type="waiting" size="20"/>
                    <span>我的面试</span>
                </p>
                <p class="two"><img src="/static/images/arrow.svg" alt=""></p>
            </div>
            <div class="myinterview">
                <p class="one">
                    <icon type="waiting" size="20"/>
                    <span>客服中心</span>
                </p>
                <p class="two"><img src="/static/images/arrow.svg" alt=""></p>
            </div>
        </div>
    </div>
</template>

<script>
export default {

}
</script>

<style>
.ownBox{
    width: 100%;
    height: 100%;
}
.own{
    width: 100%;
    height: 160px;
    display: flex;
    align-items: center;
    justify-content: center;
    background:#bac7f5;
}
.own p{
    width:60px;
    height: 60px;
    border-radius: 50%;
    background:#fff;
}
.own img{
    width:50px;
    height: 50px;
    border-radius: 50%;
    display: block;
    margin: 5px auto;
}
.listOwn{
    width: 100%;
    height: auto;
}
.myinterview{
    width:100%;
    height: 60px;
    border-bottom:1px solid #ccc;
    padding: 0 20px;
    box-sizing: border-box;
    display: flex;
    align-items: center;
    justify-content: space-between;
}
.one{
    display: flex;
    align-items: center;
}
.one span{
    margin-left: 15px;
    color:#666;
}
.two{
    margin-top: 5px;
}
.two img{
    width: 20px;
    height: 20px;
    margin-top: 5px;
}
</style>
