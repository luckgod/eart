<template>
  <div>
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
            </ul>
        </li>
      </ul>
    </div>
    
    
  </div>
</template>
<script>
export default {
  name: 'Quanbumendian',
      data () {
    return {
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
  
}
</script>
<style  scoped>
@import "Quanbumendian.css";
</style>