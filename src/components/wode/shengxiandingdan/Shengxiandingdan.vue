<template>
  <div>
       <div class="tabheader">
     <div class="tabheader_fanhui" @click="jumpa">
         <i  class="iconfont icon-left "></i>
     </div>
          <span class="tabheader_con">生鲜订单</span>
          <div class="tabheader_del" >
             <i  class="iconfont icon-kefu1"></i>
          </div>
      </div>
      <div class="warp">

       <div class="bg">
      <div class="tabh">
                <mt-navbar v-model="selected">
                    <mt-tab-item id="1" @click.native.prevent="active = 'tab1'" >全部</mt-tab-item>
                    <mt-tab-item id="2" @click.native.prevent="active = 'tab2'">待付款</mt-tab-item>
                    <mt-tab-item id="3" @click.native.prevent="active = 'tab3'" >待发货</mt-tab-item>
                    <mt-tab-item id="4" @click.native.prevent="active = 'tab4'">待收货</mt-tab-item>      
                    <mt-tab-item id="5" @click.native.prevent="active = 'tab5'">待评价</mt-tab-item>       
                </mt-navbar>
            </div>
         </div>


           <!-- tab-container -->
      <div class="tabcon">
      <div class="page-tab-container">
        <mt-tab-container class="page-tabbar-tab-container" v-model="active" >
          
            <mt-tab-container-item id="tab1">
                <div v-for="(item,index) in qb" :key="index">
                     <div class="daifukuan">
                    <div  class="daifukuan_h">
                      <ul>
                          <li class="daifukuan_tit">
                               <i class="iconfont icon-dianpu1"></i>
                                <span>{{item.storeName}}</span>
                               <i class="iconfont icon-right"></i>
                               <p>{{item.orderState|capitalize}}</p>
                          </li>
                          <li  class="daifukuan_im" >
                              <ul>
                                  <li v-for="(val,index) in item.vegetShopOrderDetails"><img  class="daifukuan_ima" :src="val.goodsIcon" alt=""></li>
                                 
                              </ul>
                          </li>
                          <li class="daifukuan_jieshuan"><span>共{{item.orderGoodsNum}}件商品 邮费¥{{item.orderFreightAmt}}    合计：<em>¥{{item.orderRealeAmt}}</em></span></li>
                      </ul>
                  </div>
                  <div class="btn_a" v-if="item.orderState=='DF'">
                      <div>
                          <p>待付款</p>
                      </div>
                      <div>
                          <p @click="quxiaota(item.orderCode)" >取消订单</p>
                      </div>
                  </div>
                  <div class="btn_a" v-if="item.orderState=='DS'">
                      <div>
                          
                      </div>
                      <div >
                          <router-link to="Shenqingtuikuan" tag="p">退款</router-link>
                      </div>
                  </div>
                   <div class="btn_a" v-if="item.orderState=='DP'">
                      <div>
                         <router-link to='Pingjia' tag="p"  :to='{path:"/Pingjia",query: {id:item.orderCode}}'>去评价</router-link>
                      </div>
                      <div>
                         
                      </div>
                  </div>
                   <div class="btn_a" v-if="item.orderState=='YP'||item.orderState=='YQ'||item.orderState=='ZQ'||item.orderState=='YT'">
                      <div>
                        
                      </div>
                      <div  :code='item.orderCode' @click="dela(item.orderCode)">
                         <p>删除订单</p>
                      </div>
                  </div>
              </div>

                
<!-- // 222222 -->
             
                  </div>
            </mt-tab-container-item>

            <mt-tab-container-item id="tab2">
             <div v-for="(item,index) in qb" :key="index" v-if="item.orderState=='DF'">
                     <div class="daifukuan">
                    <div  class="daifukuan_h">
                      <ul>
                          <li class="daifukuan_tit">
                               <i class="iconfont icon-dianpu1"></i>
                                <span>{{item.storeName}}</span>
                               <i class="iconfont icon-right"></i>
                               <p>{{item.orderState|capitalize}}</p>
                          </li>
                          <li  class="daifukuan_im" >
                              <ul>
                                  <li v-for="(val,index) in item.vegetShopOrderDetails"><img  class="daifukuan_ima" :src="val.goodsIcon" alt=""></li>
                                 
                              </ul>
                          </li>
                          <li class="daifukuan_jieshuan"><span>共{{item.orderGoodsNum}}件商品 邮费¥{{item.orderFreightAmt}}    合计：<em>¥{{item.orderRealeAmt}}</em></span></li>
                      </ul>
                  </div>
                  <div class="btn_a" v-if="item.orderState=='DF'">
                      <div>
                          <p>待付款</p>
                      </div>
                      <div>
                          <p @click="quxiaota(item.orderCode)">取消订单</p>
                      </div>
                  </div>
                  <div class="btn_a" v-if="item.orderState=='DS'">
                      <div>
                          
                      </div>
                      <div >
                          <router-link to="Shenqingtuikuan" tag="p">退款</router-link>
                      </div>
                  </div>
                   <div class="btn_a" v-if="item.orderState=='DP'">
                      <div>
                         <router-link :to='{path:'/Pingjia',query: {id:item.orderCode}}'  tag="p">去评价</router-link>
                      </div>
                      <div>
                         
                      </div>
                  </div>
                   <div class="btn_a" v-if="item.orderState=='YP'||item.orderState=='YQ'||item.orderState=='ZQ'||item.orderState=='YT'">
                      <div>
                        
                      </div>
                      <div :code='item.orderCode' @click="dela(item.orderCode)"> 
                         <p >删除订单</p>
                      </div>
                  </div>
              </div>

              </div>
              <!-- sesesesesesesesesesesesesesesesesese -->
             
            </mt-tab-container-item>

             <mt-tab-container-item id="tab3">
                  <div v-for="(item,index) in qb" :key="index" v-if="item.orderState=='DPS'">
                     <div class="daifukuan">
                    <div  class="daifukuan_h">
                      <ul>
                          <li class="daifukuan_tit">
                               <i class="iconfont icon-dianpu1"></i>
                                <span>{{item.storeName}}</span>
                               <i class="iconfont icon-right"></i>
                               <p>{{item.orderState|capitalize}}</p>
                          </li>
                          <li  class="daifukuan_im" >
                              <ul>
                                  <li v-for="(val,index) in item.vegetShopOrderDetails"><img  class="daifukuan_ima" :src="val.goodsIcon" alt=""></li>
                                 
                              </ul>
                          </li>
                          <li class="daifukuan_jieshuan"><span>共{{item.orderGoodsNum}}件商品 邮费¥{{item.orderFreightAmt}}    合计：<em>¥{{item.orderRealeAmt}}</em></span></li>
                      </ul>
                  </div>
                  <div class="btn_a" v-if="item.orderState=='DF'">
                      <div>
                          <p>待付款</p>
                      </div>
                      <div>
                          <p @click="quxiaota(item.orderCode)">取消订单</p>
                      </div>
                  </div>
                  <div class="btn_a" v-if="item.orderState=='DS'">
                      <div>
                          
                      </div>
                      <div >
                          <router-link to="Shenqingtuikuan" tag="p">退款</router-link>
                      </div>
                  </div>
                   <div class="btn_a" v-if="item.orderState=='DP'">
                      <div>
                         <router-link :to='{path:'/Pingjia',query: {id:item.orderCode}}' tag="p">去评价</router-link>
                      </div>
                      <div>
                         
                      </div>
                  </div>
                   <div class="btn_a" v-if="item.orderState=='YP'||item.orderState=='YQ'||item.orderState=='ZQ'||item.orderState=='YT'">
                      <div>
                        
                      </div>
                      <div :code='item.orderCode' @click="dela(item.orderCode)">
                         <p>删除订单</p>
                      </div>
                  </div>
              </div>

              </div>
            </mt-tab-container-item>

            <mt-tab-container-item id="tab4">
                <div v-for="(item,index) in qb" :key="index" v-if="item.orderState=='DS'">
                     <div class="daifukuan">
                    <div  class="daifukuan_h">
                      <ul>
                          <li class="daifukuan_tit">
                               <i class="iconfont icon-dianpu1"></i>
                                <span>{{item.storeName}}</span>
                               <i class="iconfont icon-right"></i>
                               <p>{{item.orderState|capitalize}}</p>
                          </li>
                          <li  class="daifukuan_im" >
                              <ul>
                                  <li v-for="(val,index) in item.vegetShopOrderDetails"><img  class="daifukuan_ima" :src="val.goodsIcon" alt=""></li>
                                 
                              </ul>
                          </li>
                          <li class="daifukuan_jieshuan"><span>共{{item.orderGoodsNum}}件商品 邮费¥{{item.orderFreightAmt}}    合计：<em>¥{{item.orderRealeAmt}}</em></span></li>
                      </ul>
                  </div>
                  <div class="btn_a" v-if="item.orderState=='DF'">
                      <div>
                          <p>待付款</p>
                      </div>
                      <div>
                          <p @click="quxiaota(item.orderCode)">取消订单</p>
                      </div>
                  </div>
                  <div class="btn_a" v-if="item.orderState=='DS'">
                      <div>
                          
                      </div>
                      <div >
                          <router-link to="Shenqingtuikuan" tag="p">退款</router-link>
                      </div>
                  </div>
                   <div class="btn_a" v-if="item.orderState=='DP'">
                      <div>
                         <router-link :to='{path:'/Pingjia',query: {id:item.orderCode}}' tag="p">去评价</router-link>
                      </div>
                      <div>
                         
                      </div>
                  </div>
                   <div class="btn_a" v-if="item.orderState=='YP'||item.orderState=='YQ'||item.orderState=='ZQ'||item.orderState=='YT'">
                      <div>
                        
                      </div>
                      <div :code='item.orderCode' @click="dela(item.orderCode)"> 
                         <p>删除订单</p>
                      </div>
                  </div>
              </div>

                </div>
            </mt-tab-container-item>

             <mt-tab-container-item id="tab5">
                     <div v-for="(item,index) in qb" :key="index" v-if="item.orderState=='DP'">
                     <div class="daifukuan">
                    <div  class="daifukuan_h">
                      <ul>
                          <li class="daifukuan_tit">
                               <i class="iconfont icon-dianpu1"></i>
                                <span>{{item.storeName}}</span>
                               <i class="iconfont icon-right"></i>
                               <p>{{item.orderState|capitalize}}</p>
                          </li>
                          <li  class="daifukuan_im" >
                              <ul>
                                  <li v-for="(val,index) in item.vegetShopOrderDetails"><img  class="daifukuan_ima" :src="val.goodsIcon" alt=""></li>
                                 
                              </ul>
                          </li>
                          <li class="daifukuan_jieshuan"><span>共{{item.orderGoodsNum}}件商品 邮费¥{{item.orderFreightAmt}}    合计：<em>¥{{item.orderRealeAmt}}</em></span></li>
                      </ul>
                  </div>
                  <div class="btn_a" v-if="item.orderState=='DF'">
                      <div>
                          <p>待付款</p>
                      </div>
                      <div>
                          <p @click="quxiaota(item.orderCode)">取消订单</p>
                      </div>
                  </div>
                  <div class="btn_a" v-if="item.orderState=='DS'">
                      <div>
                          
                      </div>
                      <div >
                          <router-link to="Shenqingtuikuan" tag="p">退款</router-link>
                      </div>
                  </div>
                   <div class="btn_a" v-if="item.orderState=='DP'">
                      <div>
                         <router-link  :to='{path:"/Pingjia",query: {id:item.orderCode}}' tag="p">去评价</router-link>
                      </div>
                      <div>
                         
                      </div>
                  </div>
                   <div class="btn_a" v-if="item.orderState=='YP'||item.orderState=='YQ'||item.orderState=='ZQ'||item.orderState=='YT'">
                      <div>
                        
                      </div>
                      <div :code='item.orderCode' @click="dela(item.orderCode)">
                         <p>删除订单</p>
                      </div>
                  </div>
              </div>

                </div>
            </mt-tab-container-item>
        </mt-tab-container>
         </div>
    </div>
   </div> 
  </div>
</template>
<script>
import { Toast } from 'mint-ui';
import { MessageBox } from 'mint-ui';
export default {
  name: 'Shengxiandingdan',
      data () {
    return {
      msg: 'moban',
       active: 'tab2',
       selected:'tab1',
       data:{
        pageNum:1,
        pageSize:10,
        sort:'ORDER_TIME',
        desc:'ASC',
        orderState:'',
        orderType:'DL'
      },
      qb:'',
      code:'',
    
    }
  },
  methods:{
      quxiaota(a){
         // MessageBox({
            // title: '提醒',
            // message: '确认取消订单?',
            // showCancelButton: true
            // });
            MessageBox.confirm('确定执行此操作?').then(action => {
                    var data={
                        orderCode:a,
                        cancleType:'S',
                        orderCancelReason:'',

                        
                    }
                this.dataApi.ajax('cancelShopOrder',data,res=>{
                 console.log('111')
                    if(res.respState=='S'){
                            Toast('取消订单成功');
                            this. weizhi()
                    }else{
                         Toast(res.respMsg);
                    }
                    
           
                })

            }).catch(function(reason) {
                Toast('已取消操作');
            });
                },
      jumpa(){
          this.$router.go(-1)
      },
       weizhi(){
          
        this.dataApi.ajax('pageShopAppOrder',this.data,res=>{
                 console.log('111')
                    if(res.respState=='S'){
                        console.log(res)
                        
                        
                         this.qb=res.vos

                    }else{
                         Toast(res.respMsg);
                    }
                    
           
                })
    },
    dela(a){
        var data={
            orderCode:a,
        }
         this.dataApi.ajax('editShopOrder',data,res=>{
                
                    if(res.respState=='S'){
                        console.log(res)
                        
                        this.weizhi()
                       

                    }else{
                         Toast(res.respMsg);
                    }
                    
           
                })
    },
     

  },
  mounted:function(){
     
     this.weizhi()
    
    
  },
  filters: {
  capitalize: function (value) {
    if(value=='DF'){
        return '待支付'
    }
     if(value=='DPS'){
        return '待配送'
    }
     if(value=='DZT'){
        return '待自提'
    }
     if(value=='DS'){
        return '待收货/待自提'
    }
     if(value=='DP'){
        return '待评价'
    }
     if(value=='ZQ'){
        return '自动取消'
    }
     if(value=='YQ'){
        return '用户已取消'
    }
    if(value=='YP'){
        return '已评价'
    }
    if(value=='YT'){
        return '已退款'
    }
  }
}
  
}
</script>
<style  scoped>
@import "Shengxiandingdan.css";
</style>