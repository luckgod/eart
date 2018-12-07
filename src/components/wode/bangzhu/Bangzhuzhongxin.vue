<template>
  <div>
      <div class="warp">
          <ul class="list">
            <li class="itm" v-for="(item,index) in qb" :key="index"  @click="jumb(item.helpCode)">
              <img :src="item.helpIcon" alt="" style="float: left;width: 0.2rem;height: 0.2rem;margin-top: 0.4rem;margin-left: 0.4rem;">
              <span>{{item.helpTitle}}</span>
              <i class="iconfont icon-right"></i>
            </li>
            
          </ul>
           <div class="btn" @click="jumpa">
                <p >意见反馈</p>
            </div>
      </div>
     
  </div>
</template>
<script>
export default {
  name: 'Bangzhuzhongxin',
      data () {
    return {
      msg: 'moban',
      data:{
        pageNum:1,
        pageSize:20,
        helpState:'Y',
      },
      qb:'',
    }
  },
  methods:{
      jumpa(){
        this.$router.push({path:'/yijianfankui'})
      },
      jumb(a){
        this.$router.push({path:'/Bangzhuxingqing',query:{id:a}})
      },
    
      weizhi(){
        this.dataApi.ajax('pageHelpCenter',this.data,res=>{
                    if(res.respState=='S'){
                        console.log(res)
                         this.qb=res.vos
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
@import "Bangzhuzhongxin.css";
</style>