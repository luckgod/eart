<template>
  <div>
      <div class="onese">
          <div class="shezhi" @click="jumpb"></div>
         
          <router-link :to="{path:'/xiaoxizhongxin',query:{tab:'tab1'}}" class="xiaoxi" tag="div"></router-link>
          <div class="gerencar">
              <div class="warpa" @click="jumpc">
                  <img class="utou" :src="userImage" alt="">
                  <div  class="warpn">
                      <p class="unam">{{userNickName}}</p>
                        <p class="upho" >{{userMobile}}</p>
                  </div>  
                </div>
                <div>
                    <div>
                            <ul class="huyu">
                                <router-link class="huyuka" to='huiyuanka' tag="li"><p>1</p> <span>会员卡</span></router-link>
                                <router-link class="huyukb" to='fukuanmaw' tag="li"><p>{{couponNumber}}</p> <span>优惠券</span></router-link>
                                <router-link class="huyukc" to="jifenshangcheng" tag="li"><p>{{userIntegral}}</p> <span>积分</span></router-link>
                            </ul>
                    </div>
                  
                    </div>
                </div> 
      </div>
      <div class="twose">
         <span>生鲜订单</span>
          <i class="iconfont icon-right twoseb"></i>
         <span>全部</span>
        
      </div>
        <div class="shenga">
                        <ul class="shengxiandingdan">
                            <router-link class="items" to="Shengxiandingdan" tag="li"><img src="../../assets/img/11.png" alt=""><p>待付款</p></router-link>
                            <li class="items"><img src="../../assets/img/12.png" alt=""><p>待发货</p></li>
                            <li class="items"><img src="../../assets/img/13.png" alt=""><p>待收货</p></li>
                            <li class="items"><img src="../../assets/img/14.png" alt=""><p>待评价</p></li>
                            <li class="items itemst"><img src="../../assets/img/15.png" alt=""><p>退款/售后</p></li>    
                        </ul>
        </div>
        <div>
            <p class="tit">常用功能</p>
            <div>
                <ul class="tita"> 
                    <router-link class="titb teshu"  to="wuyefeidikou" tag='li'><img src="../../assets/img/4.png" alt=""><p>物业缴纳</p></router-link>
                    <router-link class="titb"   to="dizhi" tag='li' ><img src="../../assets/img/5.png" alt=""><p>收货地址</p></router-link >
                    <router-link class="titb" to="huiyuanka" tag='li'><img src="../../assets/img/6.png" alt=""><p>资金管理</p></router-link>
                   
                    <router-link class="titb" to="jifenshangcheng" tag='li'><img src="../../assets/img/7.png" alt=""><p>积分商城</p></router-link>
                    <router-link class="titb"  to="bangzhuzhongxin" tag='li'><img src="../../assets/img/8.png" alt=""><p>帮助反馈</p></router-link>
                    <li class="titb"  @click="jumpe"><img src="../../assets/img/9.png" alt=""><p>客服中心</p></li>
                    <li class="titb"><img src="../../assets/img/10.png" alt=""><p>加盟合作</p></li>
                    <li class="titb"></li>
                </ul>
            </div>
        </div>
        
                   
  </div>
</template>
<script>
import { MessageBox } from 'mint-ui';
export default {
  name: 'Wode',
      data () {
    return {
      msg: 'moban',
       data:{
        
      },
      userIntegral:'',
      couponNumber:'',
      messageNumber:'',
      dfNumber:'',
      dpsNumber:'',
      dsNumber:'',
      dpNumber:'',
      userNickName:'',
      userMobile:'',
      userImage:'',
      qb:'',
    }
  },
  methods:{
     
       jumpb(){
          this.$router.push({path:'/Shezhi'})
      },
      jumpc(){
           this.$router.push({path:'/gerenziliao'})
      },
     
        jumpe(){
                    MessageBox({
                            title:'',
                            message: '+86 15268339502?',
                            showCancelButton: true,
                            confirmButtonText:'呼叫',
                            confirmButtonClass:'chanco'
                            });
      },
       weizhi(){
       
        this.dataApi.ajax('moveAppUserView',this.data,res=>{
                        console.log(res)
                    if(res.respState=='S'){
                          
                        console.log(res)
                           
                            this.userIntegral=res.userIntegral
                            this.couponNumber=res.couponNumber
                            this.dfNumber=res.dfNumber
                            this.dpsNumber=res.dpsNumber
                            this.dsNumber=res.dsNumber
                            this.dpNumber=res.dpNumber
                            this.messageNumber=res.messageNumber
                            this.userNickName=res.vegetUserVo.userNickName
                            this.userMobile=res.vegetUserVo.userMobile
                            this.userImage=res.vegetUserVo.userImage

                        
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
@import "Wode.css";
</style>