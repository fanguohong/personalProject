<template>
    <div class="interBox">
        <h3 class="msg">
            面试信息
        </h3>
        <div class="message">
            <div class="company">
                <span>公司名称</span>
                <input type="text" placeholder="请输入公司名称" class="put" @change="getCompany" :value="company">
            </div>
            <div class="company">
                <span>公司电话</span>
                <input type="number" maxlength="11" placeholder="请输入面试联系电话" class="put" @change="getPhone" :value="phone">
            </div>
            <div class="company">
                <span>面试时间</span>
                <picker
                    mode="date"
                    :value="date"
                    start="2010-10-01"
                    end="2020-12-31"
                    @change="bindDateChange"
                >
                    <span class="picker">{{date}}</span>
                </picker>
                <picker
                    mode="time"
                    :value="time"
                    start="00:00"
                    end="23:59"
                    @change="bindTimeChange"
                >
                    <span class="picker">{{time}}</span>
                </picker>
            </div>
            <div class="company">
                <span>面试地址</span>
                <p @click="address">
                    <input comfirm-type="search" placeholder="请选择面试地址" class="put" v-model="keyword" @comfirm="comfirm()" >
                </p>
            </div>
            <h3 class="msg">备注信息</h3>
            <div class="rows">
                <textarea name="area" id="area" cols="30" rows="10" placeholder="备注信息(可选，100个字以内)">
                    
                </textarea>
            </div>
            <button class="btn" style=":color:color" @click="sure">确认</button>
        </div>
    </div>
</template>

<script>
export default {
    data(){
        return{
            date:'2019-01-01',
            time:'00:00',
            company:'',
            phone:'',
            color:"#377dfd",
            allList:[]
        }
    },
    methods:{
        getCompany(e){//获取公司名称
            this.company=e.mp.detail.value;
            if(this.company.trim().length!=''){
                // console.log(this.company)
                return this.company;
            }
            
            
        },
        getPhone(e){//获取电话号码 手机号码必须11位
            this.phone=e.mp.detail.value;
            var reg = /^1[0-9]{10}$/;
            if(this.phone.trim().length && !reg.test(this.phone.trim())){
                console.log('您输入的手机号码格式不正确，请重新输入');
                return this.phone;
            }
            // console.log(this.phone)
        },
        bindDateChange(e) {//获取日期
            this.date= e.target.value  
            // console.log(this.date)
        },
        bindTimeChange(e){//获取时间
            this.time=e.target.value
            // console.log(this.time)
        },
        
        address(){
            wx.navigateTo({
                url: '/pages/search/main'
                //https://apis.map.qq.com/ws/place/v1/suggestion/?region=%E5%8C%97%E4%BA%AC&keyword=%E6%8B%9B%E8%81%98web&key=MWOBZ-T4ZLD-TP343-H3JYT-OXTES-5IBR3
            });

        },
        sure(){
            console.log('1')
            if(this.company.length){

            }
        }
    }
}
</script>

<style>
.interBox{
    width: 100%;
    height: 100%;
}
.msg{
    width: 100%;
    height: 40px;
    background:#bac7f5; 
    color: #000;
    line-height: 40px;
    padding-left: 20px;
    box-sizing: border-box;
}
.message{
    width:100%;
    height: auto;
}
.company{
    width:100%;
    height: 45px;
    border-bottom:1px solid #ccc;
    display: flex;
    align-items: center;
    padding-left: 20px;
    box-sizing: border-box;
}
.company span,#area{
    color: #777;
    font-size: 16px;
}
.put{
    width: 260px;
    height: 40px;
    margin-left: 25px;
    color: #777;
    font-size: 16px;
}
.picker{
    display: inline-block;
    margin-left: 25px;
}
.rows{
    width: 95%;
    height: 120px;
    border: 1px solid #ccc;
    margin: 15px auto;
}
#area{
    width: 100%;
    height: 100%;
    text-indent: 10px;
    padding-top: 10px;
    box-sizing: border-box;
}
.btn{
    background: #686767;
    color: #fff;
    margin-top: 30px;
}

</style>
