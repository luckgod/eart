<template>
  <div>
      <div class="warp">
          <ul class="biao">
              <li class="itema">
                  <div class="itemb">
                      <span>年份选择</span>
                  </div>
                  <div class="itemc">
                       <span style="color:#ef9310"  @click="popupVisible=!popupVisible">{{msg}}</span>
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
                       <span>环园小区</span>
                       <span><i class="iconfont icon-right"></i></span> 
                  </div>
              </li>
              <li class="itema">
                  <div class="itemb">
                      <span>物业</span>
                  </div>
                  <div class="itemc">
                       <span>凯瑞物业管理有限公司</span>
                       <span></span> 
                  </div>
              </li>
              <li class="itema">
                  <div class="itemb">
                      <span>本年应缴物业费</span>
                  </div>
                  <div class="itemc">
                       <span>¥98.00</span>
                       <span></span> 
                  </div>
              </li>
              <li class="itema">
                  <div class="itemb">
                      <span>本年已缴物业费</span>
                  </div>
                  <div class="itemc">
                       <span>¥98.00</span>
                       <span></span> 
                  </div>
              </li>
              <li class="itema">
                  <div class="itemb">
                      <span>本年未缴物业费</span>
                  </div>
                  <div class="itemc">
                       <span>¥00.00</span>
                       <span></span> 
                  </div>
              </li>
              <li class="itema">
                  <div class="itemb">
                      <span>已使用积分抵扣</span>
                  </div>
                  <div class="itemc">
                       <span>¥00.00</span>
                       <span></span> 
                  </div>
              </li>
              <li class="itema">
                  <div class="itemb">
                      <span>缴纳/抵扣详情</span>
                  </div>
                  <div class="itemc">
                       <span>查看</span>
                       <span><i class="iconfont icon-right"></i></span> 
                  </div>
              </li>
              <li class="itema">
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
    }
  },
  methods:{
      juma(){
          this.$router.push({path:'/fanghaogenggai'})
      },
       onValuesChange(picker, values) {
        // let a=picker.getValues().join(' ') 
        this.msg=values[0]
        // console.log(values)    
    },
  }
  
}
</script>
<style  scoped>
@import "Wuyefeidikou.css";
</style>