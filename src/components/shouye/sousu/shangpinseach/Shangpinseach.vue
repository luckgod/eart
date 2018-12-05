<template>
  <div>
       <div class="box">
<<<<<<< HEAD
                <input type="text" name="search" placeholder="请输入关键字" v-model="data.goodsName">
               
                <router-link  class="search" tag="div" to="/shangpinseach"  ><span @click="sera">搜索</span></router-link>
=======
                <input type="text" name="search" placeholder="请输入关键字">
               
                <router-link  class="search" tag="div" to="/shangpinseach">搜索</router-link>
>>>>>>> cd32d3b470d2fe7eb757becad960d935fdd46f19
        </div>
        <div class="two_se">
            <ul class="two_se_oul">
                <li><span>默认</span></li>
                 <li><span>销量</span></li>
                 <li  class="two_se_oulziti">
                     <span>价格</span>
<<<<<<< HEAD
                    <!-- <i class="iconfont icon-xiangshang"></i>
                    <i class="iconfont icon-xiangxia"></i> -->
=======
                    <i class="iconfont icon-xiangshang"></i>
                    <i class="iconfont icon-xiangxia"></i>
>>>>>>> cd32d3b470d2fe7eb757becad960d935fdd46f19
                </li>     
            </ul>
        </div>
        <div class="warpa">
<<<<<<< HEAD
            <ul class="con" v-for="(item,index) in qb">
                <li>
                    <ul class="itema">
                        <li class="itemaa"><img :src="item.goodsIcon" alt=""></li>
                        <li class="itemab"><span>{{item.goodsName}}</span></li>
                        <li class="itemac">
                            <div class="itemaca">
                                <span>¥{{item.goodsIsActivity=='Y'?item.goodsActivityPrice:item.goodsPrice}}</span>
                                <span v-if="item.goodsIsActivity=='Y'?true:false" >特价</span>
=======
            <ul class="con">
                <li>
                    <ul class="itema">
                        <li class="itemaa"><img src="../../../../assets/logo.png" alt=""></li>
                        <li class="itemab"><span>赣南高级脐橙2个</span></li>
                        <li class="itemac">
                            <div class="itemaca">
                                <span>¥8.80</span>
                                <span>特价</span>
                            </div>
                            <div  class="itemacb">
                               <i class="iconfont icon-gouwuche1"></i>
                            </div>
                            
                        </li>
                    </ul>
                </li>
            </ul>
             <ul class="con">
                <li>
                    <ul class="itema">
                        <li class="itemaa"><img src="../../../../assets/logo.png" alt=""></li>
                        <li class="itemab"><span>赣南高级脐橙2个</span></li>
                        <li class="itemac">
                            <div class="itemaca">
                                <span>¥8.80</span>
                                <span>特价</span>
                            </div>
                            <div  class="itemacb">
                               <i class="iconfont icon-gouwuche1"></i>
                            </div>
                            
                        </li>
                    </ul>
                </li>
            </ul>
             <ul class="con">
                <li>
                    <ul class="itema">
                        <li class="itemaa"><img src="../../../../assets/logo.png" alt=""></li>
                        <li class="itemab"><span>赣南高级脐橙2个</span></li>
                        <li class="itemac">
                            <div class="itemaca">
                                <span>¥8.80</span>
                                <span>秒杀</span>
                            </div>
                            <div  class="itemacb">
                               <i class="iconfont icon-gouwuche1"></i>
                            </div>
                            
                        </li>
                    </ul>
                </li>
            </ul>
             <ul class="con">
                <li>
                    <ul class="itema">
                        <li class="itemaa"><img src="../../../../assets/logo.png" alt=""></li>
                        <li class="itemab"><span>赣南高级脐橙2个</span></li>
                        <li class="itemac">
                            <div class="itemaca">
                                <span>¥8.80</span>
                                <span>秒杀</span>
                            </div>
                            <div  class="itemacb">
                               <i class="iconfont icon-gouwuche1"></i>
                            </div>
                            
                        </li>
                    </ul>
                </li>
            </ul>
             <ul class="con">
                <li>
                    <ul class="itema">
                        <li class="itemaa"><img src="../../../../assets/logo.png" alt=""></li>
                        <li class="itemab"><span>赣南高级脐橙2个</span></li>
                        <li class="itemac">
                            <div class="itemaca">
                                <span>¥8.80</span>
                                <span>秒杀</span>
>>>>>>> cd32d3b470d2fe7eb757becad960d935fdd46f19
                            </div>
                            <div  class="itemacb">
                               <i class="iconfont icon-gouwuche1"></i>
                            </div>
                            
                        </li>
                    </ul>
                </li>
            </ul>
<<<<<<< HEAD
             
             
             
            
<!-- DESC -降序 ASC-升序 -->
=======
>>>>>>> cd32d3b470d2fe7eb757becad960d935fdd46f19

        </div>
  </div>
</template>
<script>
export default {
  name: 'Shangpinseach',
      data () {
    return {
<<<<<<< HEAD
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
=======
      msg: 'moban'
    }
  }
>>>>>>> cd32d3b470d2fe7eb757becad960d935fdd46f19
  
}
</script>
<style  scoped>
@import "Shangpinseach.css";
</style>