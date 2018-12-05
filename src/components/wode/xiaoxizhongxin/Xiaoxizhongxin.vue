<template>
  <div>
      <div class="warp">

       <div class="bg">
      <div class="tabh">
                <mt-navbar v-model="selected">
                    <mt-tab-item id="1" @click.native.prevent="active = 'tab1'" >通知</mt-tab-item>
                    <mt-tab-item id="2" @click.native.prevent="active = 'tab2'">公告</mt-tab-item>   
                </mt-navbar>
            </div>
         </div>


           <!-- tab-container -->
      <div class="tabcon">
      <div class="page-tab-container">
        <mt-tab-container class="page-tabbar-tab-container" v-model="active" >
          
            <mt-tab-container-item id="tab1">
            <div class="yijianhuifu" v-for="(item,index) in qt" v-if="item.messageState=='R'?true:false">
                <div class="yijianhuifua">
                     <p>{{item.messageTitle}}</p>
                    <p>{{item.message}}</p>
                   
                    <p>{{item.creTime}}</p>
                </div>
            </div>
           
            </mt-tab-container-item>
            <mt-tab-container-item id="tab2">
                   <div class="yijianhuifu" v-for="(item,index) in qb" :key="index" v-if="item.sysNewsState=='Y'?true:false">
                <div class="yijianhuifua ">
                     <p>{{item.sysNewsTitle}}</p>
                    <p>{{item.sysNewsContent}}</p>                   
                    <p>{{item.sysReleaseTime}}</p>
                </div>
                <div><i class="iconfont icon-right  ziti"></i></div>
            </div>
            </mt-tab-container-item>
           
        </mt-tab-container>
         </div>
    </div>
   </div> 
  </div>
</template>
<script>
export default {
  name: 'Xiaoxizhongxin',
      data () {
    return {
      msg: 'moban',
       active: 'tab1',
       selected:'tab1',
        data:{
        pageNum:1,
        pageSize:5,
        sort:'SYS_RELEASE_TIME',
        desc:'DESC',
        pageType:'A'
      },
      qb:'',
      date:{
        pageNum:1,
        pageSize:5,
        sort:'UPD_TIME',
        desc:'DESC',
        userCode:'0000000011'

      },
      qt:'',
    }
  },
  methods:{
      weizhi(){
       
        this.dataApi.ajax('pageSysNews',this.data,res=>{
        
                    if(res.respState=='S'){
                        // console.log(res)
                        
                        
                         this.qb=res.vos
                    }else{
                         Toast(res.respMsg);
                    }
                    
           
                })
    },
    tongzhi(){
        this.dataApi.ajax('pageUserMessage',this.date,res=>{
        
                    if(res.respState=='S'){
                        console.log(res)
                         this.qt=res.vos
                    }else{
                         Toast(res.respMsg);
                    }
                    
           
                })
    }
  },
  mounted:function(){
     
     this.weizhi()
     this.tongzhi()
    
    
  },
  
}
</script>
<style  scoped>
@import "Xiaoxizhongxin.css";
</style>