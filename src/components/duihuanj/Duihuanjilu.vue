<template>
  <div>
      <div class="warp" v-for="(item,index) in qb" :key="index">
          <ul class="woul">
              <li class="itmh">
                    <span  class="itmht">兑换时间：{{item.orderTime}}</span>
                    <span class="itmhz itimepro"  :class=" peo =='未提货'  ? 'yansea' : '' ">{{peo}}{{item.orderState}}</span>
                </li>
              <li  class="woula">
                  <ul class="woulb">
                      <li class="woulimg"><img src="../../assets/logo.png" alt=""></li>
                      <li>
                          <ul>
                              <li class="wouldain">{{item.storeName}}</li>
                              <li class="wouliname">{{item.vegetShopOrderDetails[0].goodsName}}</li>
                              <li class="woulibianhao">订单编号：{{item.orderCode}}</li>
                          </ul>
                      </li>
                      <li class="woulifen">2000积分</li>
                  </ul>
              </li>
          </ul>
      </div>
      
  </div>
  <!-- DESC -降序 ASC-升序 -->
</template>

<script>
export default {
  name: 'Duihuanjilu',
      data () {
    return {
      msg: 'moban',
      peo:'未提货',
      data:{
        pageNum:1,
        pageSize:5,
        sort:'ORDER_TIME',
        desc:'DESC',
        orderType:'DG',
      },
      qb:'',
    
    }
  },
     methods:{
      weizhi(){
       
        this.dataApi.ajax('pageShopAppOrder',this.data,res=>{
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
     
     this.weizhi()
    
    
  },
  
}
</script>
<style  scoped>
@import "Duihuanjilu.css";
</style>