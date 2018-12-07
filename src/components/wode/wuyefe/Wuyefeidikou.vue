<template>
  <div>
      <div class="warp">
          <ul class="biao">
              <li class="itema">
                  <div class="itemb">
                      <span>年份选择</span>
                  </div>
                  <div class="itemc">
                       <span style="color:#ef9310"  @click="popupVisible=!popupVisible">{{date.payYear}}</span>
                       <span><i class="iconfont icon-right"></i></span>
                        <mt-popup
                        v-model="popupVisible"
                        position="bottom">
                       <mt-picker :slots="slots" @change="onValuesChange" style='width:100vw;'></mt-picker>
                      </mt-popup> 
                  </div>
              </li>
              <li class="itema" @click="juma">
                  <div class="itemb">
                      <span>小区房号</span>
                  </div>
                  <div class="itemc">
                       <span>{{estateName}}</span>
                       <span><i class="iconfont icon-right"></i></span> 
                  </div>
              </li>
              <li class="itema">
                  <div class="itemb">
                      <span>物业</span>
                  </div>
                  <div class="itemc">
                       <span>{{propertyName}}</span>
                       <span></span> 
                  </div>
              </li>
              <li class="itema">
                  <div class="itemb">
                      <span>本年应缴物业费</span>
                  </div>
                  <div class="itemc">
                       <span>¥{{mustCosts}}</span>
                       <span></span> 
                  </div>
              </li>
              <li class="itema">
                  <div class="itemb">
                      <span>本年已缴物业费</span>
                  </div>
                  <div class="itemc">
                       <span>¥{{mustCosts-unpaidCosts}}</span>
                       <span></span> 
                  </div>
              </li>
              <li class="itema">
                  <div class="itemb">
                      <span>本年未缴物业费</span>
                  </div>
                  <div class="itemc">
                       <span>¥{{unpaidCosts}}</span>
                       <span></span> 
                  </div>
              </li>
              <li class="itema">
                  <div class="itemb">
                      <span>已使用积分抵扣</span>
                  </div>
                  <div class="itemc">
                       <span>¥{{integralCosts}}</span>
                       <span></span> 
                  </div>
              </li>
              <li class="itema" @click="jump">
                  <div class="itemb">
                      <span>缴纳/抵扣详情</span>
                  </div>
                  <div class="itemc">
                       <span>查看</span>
                       <span><i class="iconfont icon-right"></i></span> 
                  </div>
              </li>
              <li class="itema" @click="jumpb">
                  <div class="itemb">
                      <span>物业费缴纳说明</span>
                  </div>
                  <div class="itemc">
                       <span>查看</span>
                       <span><i class="iconfont icon-right"></i></span> 
                  </div>
              </li>
            
          </ul>
      </div>
    <router-link class="btn" to="Wuyejiaona" tag="div">
        <p >缴纳/抵扣物业费</p>
    </router-link> 
  </div>
</template>
<script>
import { Toast } from 'mint-ui';
import { DatetimePicker } from 'mint-ui';
import { Popup } from 'mint-ui';
export default {
  name: 'Wuyefeidikou',
      data () {
    return {
      msg:'',
       popupVisible:false,
        slots: [
        {
          flex: 1,
          values: ['2018', '2019', '2020', '2021', '2022', '2023','2024','2025','2026'],
          className: 'slot1',
          textAlign: 'center'
        },

      ],
      date:{
          payYear:'2018'
      },
      estateName:'',
      propertyName:'',
      mustCosts:'',
      unpaidCosts:'',
      integralCosts:'',        
    }
  },
  methods:{
      juma(){
          this.$router.push({path:'/fanghaogenggai'})
      },
      jump(){
          this.$router.push({path:'/Dikouxiangqing'})
      },
      jumpb(){
          this.$router.push({path:'/Jiaonashuoming'})
      },
       onValuesChange(picker, values) {
        // let a=picker.getValues().join(' ') 
        this.date.payYear=values[0]
         this.weizhi()
        // console.log(values)    
    },
    weizhi(){
       
        this.dataApi.ajax('userWuYe',this.date,res=>{
                // console.log('111')
                // console.log(this.date.payYear)
                    if(res.respState=='S'){
                        console.log(res)
                        this.estateName=res.estateName
                        this.propertyName=res.propertyName
                        this.mustCosts=res.mustCosts
                        this.unpaidCosts=res.unpaidCosts
                        this.integralCosts=res.integralCosts
                       
                        
                        //  this.qb=res.vos
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
@import "Wuyefeidikou.css";
</style>