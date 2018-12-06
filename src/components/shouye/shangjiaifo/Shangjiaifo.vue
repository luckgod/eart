<template>
  <div>
 <div class="tabheader">
     <div class="tabheader_fanhui" @click="jumpa">
         <i  class="iconfont icon-left "></i>
     </div>
          <span class="tabheader_con">{{storeName}}</span>
          <router-link class="tabheader_del" to='quanbumendian' tag="div">
              <span>全部门店</span>
          </router-link>
      </div>
    <div class="tab">

   
        <mt-navbar v-model="selected">
            <mt-tab-item id="1"  @click.native.prevent="active = 'tab-container1'" :class="active=='tab-container1'?'is-selected':''">商家</mt-tab-item>
            <mt-tab-item id="2"  @click.native.prevent="active = 'tab-container2'" :class="active=='tab-container2'?'is-selected':''">评价</mt-tab-item>
            <mt-tab-item id="3"  @click.native.prevent="active = 'tab-container3'" :class="active=='tab-container3'?'is-selected':''">领券</mt-tab-item>
        </mt-navbar>
     </div>    
    <div class="page-tab-container">
      <mt-tab-container class="page-tabbar-tab-container" v-model="active" >
        <mt-tab-container-item id="tab-container1" >
        	<ul class="shajia" style="font-size:0.26rem;margin-left:0.4rem; line-height: 0.9rem; color: #666666;">
                <li> <i style=" margin-right: 0.16rem" class="iconfont icon-Group- "></i><span style=" text-indent:0.16rem;">{{storeAddress}}</span></li>
                <li> <i style=" margin-right: 0.16rem" class="iconfont icon-shijian "></i><span style=" text-indent:0.16rem; ">营业时间：{{storeBusHouse}}</span></li>
                <li> <i style=" margin-right: 0.16rem" class="iconfont icon-weibiaoti- "></i><span style=" text-indent:0.16rem; ">联系方式：{{storePhone}}</span></li>
                <li> <i style=" margin-right: 0.16rem" class="iconfont icon-gouwudai201 "></i><span style=" text-indent:0.16rem; ">已售：{{storeSold}} 件</span></li>
                <li v-if="storeIsDis=='Y'? true:false"> <i style=" margin-right: 0.16rem" class="iconfont icon-wodeyouhuijuan "></i><span style=" text-indent:0.16rem; ">起送：¥{{storeRiseDistFee}}元  配送：¥{{storeDistFee}}元</span></li>
                 <li v-if="storeIsDis=='N'? true:false"> <i style=" margin-right: 0.16rem" class="iconfont icon-wodeyouhuijuan "></i><span style=" text-indent:0.16rem; ">暂不支持配送</span></li>
                
            </ul>   
        </mt-tab-container-item>
        <mt-tab-container-item id="tab-container2" >
        	<!-- cell组件 -->
         <div v-bind:class="{ pingjun: isActive }">
             <div v-bind:class="{pingfen:true}"  style="text-indent: 0.2rem">
                 <span> {{evaluateStar}}</span>
             </div>
             <div  v-bind:class="{fll:true}">
             <div>
                <img v-for="(star,index) in stars" v-bind:src="star.src" :key="index" v-bind:class="{pingfen_tu:true}"/>
                {{reversedMessage}}
                  
             </div>
             <div  v-bind:class="{pingfen_h:true}">
                 <span v-bind:class="{pingfen_t:true}">真实评价</span>    
             </div>
             </div>

         </div>
         <!-- pinglu -->
         <div :class="{renping:true}" v-for="(item,index) in pj" :key="index">
             <ul :class="{renping_oul:true}"  >
                 <li >
                     <ul  :class="{renping_oul:true}" >
                         <li  :class="{fll:true}"><img src="../../../assets/logo.png" :class="{renping_touxing:true}"></li>
                        <li :class="{flr:true}">
                            <ul  >
                                <li>
                                    <ul :class="{fll:true}"  style="width:5.5rem;height:0.44rem">
                                        <li :class="{renping_yonghuming:true,fll:true}">{{item.userNickName}}</li>
                                        <li>
                                            <div>
                                                <img v-for="(star,index) in stars" v-bind:src="star.src" :key="index" v-bind:class="{pingfen_tu:true,flr:true}"/>
                                                {{reversedMessage}}
                                                
                                            </div>
                                        </li>
                                    </ul>
                                </li>
                                <li><span v-bind:class="{pingfen_shijian:true,fll:true}">{{item.evaluateTime}}</span></li>
                            </ul>
                        </li>
                     </ul>
                 </li>
                  <li :class="{pl:true}"  >{{item.evaluateContent}}</li>
                 
                 <li>
                     <ul>
                         <li  v-for="(item,index) in item.vegetImageVos" :key="index"><img :class="{fll:true,zhenshizhaopian:true}" :src="item.imageAddress" ></li>
                        
                     </ul>
                 </li> 
             </ul>
         </div>
         <!-- pinglu -->
         
        </mt-tab-container-item>
        <mt-tab-container-item id="tab-container3"  >
        	<!-- juan  'couponState'-->
            <div class="youhuijuan" v-for="(item,index) in couponVos" :key="index" >
                <div class="banyuana"></div>
                <div class="banyuanb"></div>
                <div class="youhuijuannei"  >
                    <div class="youhuijuanneifenge">
                        <div class="youhuijuanmianzhi">￥{{item.couponAmt}}</div>
                        <div class="youhuijuanbtn" >领取</div>
                    </div>
                    <div class="flra">
                        <p class="youhuijuanmainshua">{{item.couponName}}</p>
                        <p class="youhuijuanmainshub">可与积分同时使用</p>
                        <p class="youhuijuanmainshub">有效期至{{item.couponEtime}}</p>
                    </div>
                </div>
            </div>
            
            
        </mt-tab-container-item>
      </mt-tab-container>
    </div>


</div>
</template>
<script>
import { Toast } from 'mint-ui';
import bo from "../../../assets/bolunan.png"
import boa from "../../../assets/boluu.png"
var starOffImg = bo;
var starOnImg = boa;
export default {
  name: 'Shangjiaifo',
      data () {
    return {
    storeCode:'',
    msg: 'moban',
    active:'tab-container1',
    selected:1,
    isActive:true,
    stars: [{
                            src: starOffImg,
                            active: false
                        }, {
                            src: starOffImg,
                            active: false
                        }, {
                            src: starOffImg,
                            active: false
                        },
                        {
                            src: starOffImg,
                            active: false
                        }, {
                            src: starOffImg,
                            active: false
                        }
                    ],
                    starNum: 5,
                    data:{
                        storeCode:'',
                        pageNum:1,
                        pageSize:5,
                    },
                    storeName:'',
                    storeAddress:'',
                    storeBusHouse:'',
                    storePhone:'',
                    couponVos:[],
                    storeRiseDistFee:'',
                    storeDistFee:'',
                    storeSold:'',
                    storeIsDis:'',
                    evaluateStar:"",
                    pj:'',

    }
   
    
  },
  methods: {
            jumpa(){
                this.$router.go(-1)
                },
            shangjia(){
                this.data.storeCode=this.$route.query.storeCode
                // console.log(this.storeCode)
                this.dataApi.ajax('detailStore',this.data,res=>{
                    if(res.respState=='S'){
                        // console.log(res)
                        
                        this.storeName=res.storeName
                        this.storeAddress=res.storeAddress
                        this.storeBusHouse=res.storeBusHouse
                        this.storePhone=res.storePhone
                        this.couponVos=res.couponVos
                        this.storeRiseDistFee=res.storeRiseDistFee
                        this.storeDistFee=res.storeDistFee
                        this.storeSold=res.storeSold
                        this.storeIsDis=res.storeIsDis
                      
                    }else{
                        
                        Toast(res.respMsg);
                    }
                    
           
                })
            },
            pinngjia(){
                this.data.storeCode=this.$route.query.storeCode
               
                this.dataApi.ajax('pageEvaluate',this.data,res=>{
                    if(res.respState=='S'){
                        console.log(res)
                        this.evaluateStar=res.evaluateStar
                        this.starNum=Math.ceil(res.evaluateStar)
                        this.pj=res.vos
                    }else{
                         Toast(res.respMsg);
                    }
                    
           
                })
            },
           

  },
  mounted:function(){
     
    this.shangjia()
    this.pinngjia()
      
     this.active=this.$route.query.num
    
  },
  computed: {
    
    reversedMessage: function () {
      
       
        for(var i = 0; i < this.starNum; i++) {
            this.stars[i].src = starOnImg;
            this.stars[i].active = true;
    }
                            
    }
  }           
    
  
}
</script>
<style  scoped>
@import "Shangjiaifo.css";
</style>