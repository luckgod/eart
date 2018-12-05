<template>
  <div>
    <div class="tabheader">
     <div class="tabheader_fanhui" @click="fanhui">
         <i  class="iconfont icon-left " ></i>
     </div>
          <span class="tabheader_con" >积分商城</span>
          <router-link  to='jiaoyimingxi'  class="tabheader_del" tag="div" >
              <span>积分明细</span>
          </router-link>
      </div>
    <div class="dangqianjinfen">
      <div class="dangqianjinfenl">
        <span class="dangqianjinfenls">688</span>
        <span class="dangqianjinfenla">当前积分</span>
      </div>
      
      <div class="dangqianjinfenr">
        <router-link class="dangqianjinfenrz" tag="span" to="/duihuanjilu">兑换记录</router-link> 
      </div>
    </div>
    <div>
      <div class="xiaoqut"> 
        <span class="xiaoqu">水天成小区</span>
      </div>
    </div>
    <div>
      <div class="duihua">
        <ul>
<<<<<<< HEAD
          <router-link tag="li" class="kau" :to="{path:'/jfenduihuan'}" v-for="(item,index) in qb" :key="index">
         
            <img  class="jiimg" :src="item.goodsIcon" alt="">
            <p class="jiname">{{item.goodsName}}</p>
            <p class="jinaf">{{item.goodsIntegralPrice}}积分</p>
          </router-link>
         
=======
          <router-link tag="li" class="kau" :to="{path:'/jfenduihuan'}">
         
            <img  class="jiimg" src="../../../assets/logo.png" alt="">
            <p class="jiname">水果拼盘</p>
            <p class="jinaf">100积分</p>
          </router-link>
          <router-link tag="li" class="kau" :to="{path:'/jfenduihuan'}">
         
            <img  class="jiimg" src="../../../assets/logo.png" alt="">
            <p class="jiname">水果拼盘</p>
            <p class="jinaf">100积分</p>
          </router-link>
          <router-link tag="li" class="kau" :to="{path:'/jfenduihuan'}">
         
            <img  class="jiimg" src="../../../assets/logo.png" alt="">
            <p class="jiname">水果拼盘</p>
            <p class="jinaf">100积分</p>
          </router-link>
          <router-link tag="li" class="kau" :to="{path:'/jfenduihuan'}">
         
            <img  class="jiimg" src="../../../assets/logo.png" alt="">
            <p class="jiname">水果拼盘</p>
            <p class="jinaf">100积分</p>
          </router-link>
          <router-link tag="li" class="kau" :to="{path:'/jfenduihuan'}">
         
            <img  class="jiimg" src="../../../assets/logo.png" alt="">
            <p class="jiname">水果拼盘</p>
            <p class="jinaf">100积分</p>
          </router-link>
          <router-link tag="li" class="kau" :to="{path:'/fenlei'}">
         
            <img  class="jiimg" src="../../../assets/logo.png" alt="">
            <p class="jiname">水果拼盘</p>
            <p class="jinaf">100积分</p>
          </router-link>
>>>>>>> cd32d3b470d2fe7eb757becad960d935fdd46f19
                  
        </ul>
      </div>
    </div>
  </div>
</template>
<script>
export default {
  name: 'Jifenshangcheng',
      data () {
    return {
      msg: 'moban',
<<<<<<< HEAD
      data:{
        pageNum:1,
        pageSize:5,
        goodsName:'',
        storeCode:'S0000000000',
        sort:'UPD_TIME',
        desc:'ASC',
        goodsType:'G',
        goodsState:'U',
      },
      
      qb:'',
=======
>>>>>>> cd32d3b470d2fe7eb757becad960d935fdd46f19
     
    }
  },
  methods:{
     fanhui(){
        this.$router.go(-1)
        
<<<<<<< HEAD
     },
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
@import "Jifenshangcheng.css";
</style>