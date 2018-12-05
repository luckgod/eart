<template>
  <div>
    
    <div class="lunbo">
        <mt-swipe :auto="4000" style="width:6.6rem;height:2.9rem;margin:0 auto;">
            <mt-swipe-item><img :src="msg" alt="" class="kimg"></mt-swipe-item>
        </mt-swipe>
    </div>
    <div class="proa" v-for="(item,index) in qb">
        <ul class="proaoul">
            <!-- style="border:1px solid black" -->
            <li class="proaoula"><img :src="item.goodsIcon" alt="" class="proaomg"></li>
            <li class="proaoulb">
                <ul>
                    <li class="proatit"><span >{{item.goodsName}}</span></li>
                    <li class="proayishou"><span >已售{{item.goodsRetailVolume}}</span></li>
                    <li class="proaqian"><span >¥{{item.goodsIsActivity=='Y'?item.goodsActivityPrice:item.goodsPrice}}</span><i class="iconfont icon-gouwuche ziti"></i></li>
                </ul>
            </li>
        </ul>
    </div>

     
  </div>
</template>
<script>
export default {
  name: 'Laingdanghuodong',
      data () {
    return {
      msg: '',
       data:{
        storeCode:'S0000000000',
        operateCode:'DBCCB653F2E0446492668AAD460838DA',
       
      },
      qb:'',
    }
  },
  methods:{
      weizhi(){
       
        this.dataApi.ajax('operateGoods',this.data,res=>{
         
                    if(res.respState=='S'){
                        console.log(res)
                        
                        
                         this.qb=res.vos
                    }else{
                         Toast(res.respMsg);
                    }
                    
           
                })
    },
    huoqu(){
       
        this.msg=this.$route.query.tu
    }
  },
  mounted:function(){
     
     this.weizhi()
     this.huoqu()
    
    
  },
  
}
</script>
<style  scoped>
@import "Laingdanghuodong.css";
</style>