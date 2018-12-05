<template>
  <div>
       <div class="box">
                <input type="text" name="search" placeholder="请输入关键字" v-model="data.goodsName">
               
                <router-link  class="search" tag="div" to="/shangpinseach"  ><span @click="sera">搜索</span></router-link>
        </div>
        <div class="two_se">
            <ul class="two_se_oul">
                <li><span>默认</span></li>
                 <li><span>销量</span></li>
                 <li  class="two_se_oulziti">
                     <span>价格</span>
                    <!-- <i class="iconfont icon-xiangshang"></i>
                    <i class="iconfont icon-xiangxia"></i> -->
                </li>     
            </ul>
        </div>
        <div class="warpa">
            <ul class="con" v-for="(item,index) in qb">
                <li>
                    <ul class="itema">
                        <li class="itemaa"><img :src="item.goodsIcon" alt=""></li>
                        <li class="itemab"><span>{{item.goodsName}}</span></li>
                        <li class="itemac">
                            <div class="itemaca">
                                <span>¥{{item.goodsIsActivity=='Y'?item.goodsActivityPrice:item.goodsPrice}}</span>
                                <span v-if="item.goodsIsActivity=='Y'?true:false" >特价</span>
                            </div>
                            <div  class="itemacb">
                               <i class="iconfont icon-gouwuche1"></i>
                            </div>
                            
                        </li>
                    </ul>
                </li>
            </ul>
             
             
             
            
<!-- DESC -降序 ASC-升序 -->

        </div>
  </div>
</template>
<script>
export default {
  name: 'Shangpinseach',
      data () {
    return {
      msg: 'moban',
      data:{
        pageNum:1,
        pageSize:5,
        goodsName:'',
        storeCode:'S0000000000',
        sort:'UPD_TIME',
        desc:'ASC',
        goodsType:'S',
        goodsState:'U',
      },
      value:'',
      qb:'',
    }
  },
   methods:{
      weizhi(){
          console.log(this.data)
        this.dataApi.ajax('pageStoreGoods',this.data,res=>{
                  
                    if(res.respState=='S'){
                        console.log(res)
                          console.log('111')
                        
                         this.qb=res.vos
                    }else{
                         Toast(res.respMsg);
                    }
                    
           
                })
        },
        sera(){
          
            console.log(this.data.goodsName)
             this.weizhi()
        }
  },
  mounted:function(){
     
     this.weizhi()
  },
  
}
</script>
<style  scoped>
@import "Shangpinseach.css";
</style>