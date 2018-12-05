<template>
  <div>
<<<<<<< HEAD
    <div class="mencar" v-for="(item,index) in qb" :key="index">
      <ul>
        <li class="fll"><img :src="item.storeIcon" alt="" class="mendianimg"></li>
        <li class="fll">
            <ul class="mencarr">
                  <li class="mencartit">{{item.storeName}}</li>
                  <li class="mencartitwo" > <img src="../../assets/boluu.png" alt=""><span>{{item.evaluateStar}}分</span><span>已售{{item.storeSold}}</span></li>
                  <li  class="mencartithe" v-if="item.storeIsDis=='Y'?true:false"><span>起送¥{{item.storeRiseDistFee}} 配送¥{{item.storeDistFee}}</span><span>{{item.storeDistance}}km</span></li>
                   <li  class="mencartithe" v-if="item.storeIsDis=='N'?true:false"><span>起送¥{{item.storeRiseDistFee}} 配送¥{{item.storeDistFee}}</span><span>{{item.storeDistance}}km</span></li>
                  <li class="mencartifour"><span>{{item.storeAddress}}</span></li>
=======
    <div class="mencar">
      <ul>
        <li class="fll"><img src="../../assets/logo.png" alt="" class="mendianimg"></li>
        <li class="fll">
            <ul class="mencarr">
                  <li class="mencartit">太阳公社水天成分店</li>
                  <li class="mencartitwo"> <img src="../../assets/boluu.png" alt=""><span>4.8分</span><span>已售1012</span></li>
                  <li  class="mencartithe"><span>起送¥20 配送¥5</span><span>2.0km</span></li>
                  <li class="mencartifour"><span>萧山区钱江世纪城飞虹路222号</span></li>
            </ul>
        </li>
      </ul>
    </div>
    <div class="mencar">
      <ul>
        <li class="fll"><img src="../../assets/logo.png" alt="" class="mendianimg"></li>
        <li class="fll">
            <ul class="mencarr">
                  <li class="mencartit">太阳公社水天成分店</li>
                  <li class="mencartitwo"> <img src="../../assets/boluu.png" alt=""><span>4.8分</span><span>已售1012</span></li>
                  <li  class="mencartithe"><span>起送¥20 配送¥5</span><span>2.0km</span></li>
                  <li class="mencartifour"><span>萧山区钱江世纪城飞虹路222号</span></li>
            </ul>
        </li>
      </ul>
    </div>
    <div class="mencar">
      <ul>
        <li class="fll"><img src="../../assets/logo.png" alt="" class="mendianimg"></li>
        <li class="fll">
            <ul class="mencarr">
                  <li class="mencartit">太阳公社水天成分店</li>
                  <li class="mencartitwo"> <img src="../../assets/boluu.png" alt=""><span>4.8分</span><span>已售1012</span></li>
                  <li  class="mencartithe"><span>起送¥20 配送¥5</span><span>2.0km</span></li>
                  <li class="mencartifour"><span>萧山区钱江世纪城飞虹路222号</span></li>
            </ul>
        </li>
      </ul>
    </div>
    <div class="mencar">
      <ul>
        <li class="fll"><img src="../../assets/logo.png" alt="" class="mendianimg"></li>
        <li class="fll">
            <ul class="mencarr">
                  <li class="mencartit">太阳公社水天成分店</li>
                  <li class="mencartitwo"> <img src="../../assets/boluu.png" alt=""><span>4.8分</span><span>已售1012</span></li>
                  <li  class="mencartithe"><span>起送¥20 配送¥5</span><span>2.0km</span></li>
                  <li class="mencartifour"><span>萧山区钱江世纪城飞虹路222号</span></li>
>>>>>>> cd32d3b470d2fe7eb757becad960d935fdd46f19
            </ul>
        </li>
      </ul>
    </div>
<<<<<<< HEAD
    
    
=======
>>>>>>> cd32d3b470d2fe7eb757becad960d935fdd46f19
  </div>
</template>
<script>
export default {
  name: 'Quanbumendian',
      data () {
    return {
<<<<<<< HEAD
      msg: 'moban',
      data:{
        pageNum:1,
        pageSize:5,
        localPrecision:'120.231784',
        localDimension:'30.197081',
      },
      qb:'',
    }
  },
  methods: {
    qunbu(){
       
        this.dataApi.ajax('pageStore',this.data,res=>{
          console.log('111')
                    if(res.respState=='S'){
                        console.log(res)
                        
                        
                         this.qb=res.vos
                    }else{
                         Toast(res.respMsg);
                    }
                    
           
                })
    },
    
   
  },
  mounted:function(){
     
     this.qunbu()
    
    
  },
=======
      msg: 'moban'
    }
  }
>>>>>>> cd32d3b470d2fe7eb757becad960d935fdd46f19
  
}
</script>
<style  scoped>
@import "Quanbumendian.css";
</style>