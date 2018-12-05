<template>
  <div>
    <div  class="once">

   
      <div>
        <div class="one_se_tip">
          当前位置
        </div>
        <div class="one_se_wz">
          <ul>
            <li class="one_se_shu ">德信AI产业园</li>
            <li class="one_se_zuo"><i class="iconfont icon-dingwei"></i><span>重新定位</span></li>
          </ul>
        </div>
      </div>
      <div>
        <div class="one_se_tip">
          附近门店
        </div>
        <div class="one_se_wz" v-for="(item,index) in qb" :key="index">
          <ul>
            <li class="one_se_shu" >{{item.storeName}}</li>
            <li class="one_se_zuo"><span>前往选购</span><i class="iconfont icon-right big"></i></li>
          </ul>
        </div>
       
      </div>
      </div> 
  </div>
</template>
<script>
export default {
     name: 'Huoquweizhi',
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
  methods:{
      weizhi(){
       
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
     
     this.weizhi()
    
    
  },
  
}
</script>
<style  scoped>
@import "Huoquweizhi.css";
</style>