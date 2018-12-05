<template>
  <div>
<<<<<<< HEAD
      <div class="warp" v-for="(item,index) in qb" :key="index">
          <ul class="woul">
              <li class="itmh">
                    <span  class="itmht">兑换时间：{{item.orderTime}}</span>
                    <span class="itmhz itimepro"  :class=" peo =='未提货'  ? 'yansea' : '' ">{{peo}}{{item.orderState}}</span>
=======
      <div class="warp">
          <ul class="woul">
              <li class="itmh">
                    <span  class="itmht">兑换时间：2018-09-20 16:12:30</span>
                    <span class="itmhz itimepro"  :class=" peo =='未提货'  ? 'yansea' : '' ">{{peo}}</span>
>>>>>>> cd32d3b470d2fe7eb757becad960d935fdd46f19
                </li>
              <li  class="woula">
                  <ul class="woulb">
                      <li class="woulimg"><img src="../../assets/logo.png" alt=""></li>
                      <li>
                          <ul>
<<<<<<< HEAD
                              <li class="wouldain">{{item.storeName}}</li>
                              <li class="wouliname">{{item.vegetShopOrderDetails[0].goodsName}}</li>
                              <li class="woulibianhao">订单编号：{{item.orderCode}}</li>
=======
                              <li class="wouldain">水天成2号店</li>
                              <li class="wouliname">赣南高级脐橙2个</li>
                              <li class="woulibianhao">订单编号：2873648972672</li>
                          </ul>
                      </li>
                      <li class="woulifen">2000积分</li>
                  </ul>
              </li>
          </ul>
      </div>
       <div class="warp">
          <ul class="woul">
              <li class="itmh">
                    <span  class="itmht">兑换时间：2018-09-20 16:12:30</span>
                    <span class="itmhz">已提货</span>
                </li>
              <li  class="woula">
                  <ul class="woulb">
                      <li class="woulimg"><img src="../../assets/logo.png" alt=""></li>
                      <li>
                          <ul>
                              <li class="wouldain">水天成2号店</li>
                              <li class="wouliname">赣南高级脐橙2个</li>
                              <li class="woulibianhao">订单编号：2873648972672</li>
>>>>>>> cd32d3b470d2fe7eb757becad960d935fdd46f19
                          </ul>
                      </li>
                      <li class="woulifen">2000积分</li>
                  </ul>
              </li>
          </ul>
      </div>
<<<<<<< HEAD
      
  </div>
  <!-- DESC -降序 ASC-升序 -->
</template>

=======
  </div>
</template>
>>>>>>> cd32d3b470d2fe7eb757becad960d935fdd46f19
<script>
export default {
  name: 'Duihuanjilu',
      data () {
    return {
      msg: 'moban',
      peo:'未提货',
<<<<<<< HEAD
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
=======
    }
  }
>>>>>>> cd32d3b470d2fe7eb757becad960d935fdd46f19
  
}
</script>
<style  scoped>
@import "Duihuanjilu.css";
</style>