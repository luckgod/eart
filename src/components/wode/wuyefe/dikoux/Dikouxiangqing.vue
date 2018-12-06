<template>
  <div>
      <div class="warp">
          <ul>
              <li  class="oli" v-for="(item,index) in qb" :key="index">
                  <p class="shuoming">使用{{item.payIntegral}}个积分抵扣业务费{{item.payIntegral/item.payIntegralRatio}}元</p>
                  <p class="shijian">{{item.payTime}}</p>
                   <p class="dingwei">-{{item.payIntegral/item.payIntegralRatio+item.payCash}}物业费</p>
              </li>
              
          </ul>
      </div>
  </div>
</template>
<script>
export default {
  name: 'Dikouxiangqing',
      data () {
    return {
      msg: 'moban',
       data:{
        pageNum:1,
        pageSize:5,
        roomCode:'0D6A18E0174247E1B1506D49BF21DE21',
      },
      qb:'',
    }
  },
   methods:{
      weizhi(){
       
        this.dataApi.ajax('pageUserPayment',this.data,res=>{
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
@import "Dikouxiangqing.css";
</style>