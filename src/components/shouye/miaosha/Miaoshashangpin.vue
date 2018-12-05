<template>
  <div>
      <div class="miaosh-he"> 
          <span>限时抢购中</span>
          <span class="miaosh_her">距结束</span>
          <div class="shijian">
              <span class="shijiana">{{hr}}</span>
              <span >:</span>
              <span class="shijiana">{{min}}</span>
              <span>:</span>
              <span class="shijiana">{{sec}}</span>
              
          </div>
          
      </div>
      <div class="cara" v-for="(item,index) in qb">
          <ul class="carim">
              <li>
                  <img :src="item.goodsIcon" alt="">
              </li>
              <li class="cara_miao">
                <p class="cara_miaoa">{{item.goodsExplain}}</p>
                <p class="cara_miaob">已售{{item.goodsRetailVolume}}个 </p>
                <div>
                <span class="cara_jia">￥{{item.goodsIsActivity=='Y'?item.goodsActivityPrice:item.goodsPrice}}</span>
                <i class="iconfont icon-gouwuche ziti"></i>
                </div>
              </li>
          </ul>
      </div>
        
  </div>
</template>
<script>
export default {
  name: 'Miaoshashangpin',
      data () {
    return {
      msg: 'miaoihsa',
       data:{
        storeCode:'S0000000000',
        promoCode:'795739EE202247D5BBD14B4A5216B92D',
       
      },
      qb:'',
      endtime:'',
        day: 0, 
      hr: 0,
      min: 0,
      sec: 0,
    }
  },
   methods:{
      weizhi(){
       
        this.dataApi.ajax('promotionGoods',this.data,res=>{
          console.log(res)
                    if(res.respState=='S'){
                    this.endtime=res.promoEndTime
                         this.qb=res.vos
                         this.countdown()
                    }else{
                         Toast(res.respMsg);
                    }
                    
           
                })
    },
    countdown: function () {
      const end = Date.parse(new Date(this.endtime))
      const now = Date.parse(new Date())
      const msec = end - now
      let day = parseInt(msec / 1000 / 60 / 60 / 24)
      let hr = parseInt(msec / 1000 / 60 / 60 % 24)
      let min = parseInt(msec / 1000 / 60 % 60)
      let sec = parseInt(msec / 1000 % 60)
      this.day = day
      this.hr = hr > 9 ? hr : '0' + hr
      this.min = min > 9 ? min : '0' + min
      this.sec = sec > 9 ? sec : '0' + sec
      const that = this
      setTimeout(function () {
        that.countdown()
      }, 1000)
    },
  },
  mounted:function(){
     
     this.weizhi()
    
    
  },
  
}
</script>
<style  scoped>
@import "Miaoshashangpin.css";
</style>