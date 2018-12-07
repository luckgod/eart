<template>
  <div>
      <div class="warp">
           <ul class="biao">
              <li class="itema" >
                  <div class="itemb">
                      <span>本年应缴物业费</span>
                  </div>
                  <div class="itemc">
                       <span>¥98.00</span>
                       <span></span> 
                  </div>
              </li>
               <!-- <li class="itema" >
                  <div class="itemb">
                      <span>可用50积分抵用5元</span>
                  </div>
                  <div class="itemc diana">
                       <div class="dingwei">
                         <input class="switch switch-anim" type="checkbox" checked>
                          </div>
                  </div>
              </li> -->
               <li class="itema" >
                  <div class="itemb">
                      <span>输入抵扣积分(可用<span style="color: rgb(239, 147, 16);">5000</span>积分)</span>
                  </div>
                  <div class="itemc">
                       <span><input type="text" style="border-bottom:1px solid #000; width:1rem;"> 元</span>
                       <span></span> 
                  </div>
              </li>
              <li class="itema" >
                  <div class="itemb">
                      <span>可抵扣物业费</span>
                  </div>
                  <div class="itemc">
                       <span>5 元</span>
                       <span></span> 
                  </div>
              </li>
              <li class="itema" >
                  <div class="itemb">
                      <span>积分不够现金来凑</span>
                  </div>
                  <div class="itemc">
                       <span>93 元</span>
                       <span></span> 
                  </div>
              </li>
            <li class="itema itemba" >
                  <div class="itemb ">
                      <span>支付方式</span>
                  </div>
                 
            </li>
               <li class="itema diangw" >
                  <div class="itemb">
                     <i class="iconfont icon-weixinzhifu zitia"></i>
                     <div class="zhifua">
                         <span>微信支付</span>
                    </div> 
                  </div>
                 <div class="dingweiwe">
                    <div class="radio" > 
                            <label>
                                <input type="radio" name="sex" value="" />
                                <div class="option"></div><!--该div盛放的是优化后的按钮图片-->
                            
                            </label>
                        </div>
                    </div> 
              </li>
                <li class="itema diangw" >
                  <div class="itemb">
                     <i class="iconfont icon-big-Pay zitib"></i>
                     <div class="zhifub">
                         <span>支付宝</span>
                    </div> 
                  </div>
                 <div class="dingweiwe">
                    <div class="radio" > 
                            <label>
                                <input type="radio" name="sex" value="" />
                                <div class="option"></div><!--该div盛放的是优化后的按钮图片-->
                            
                            </label>
                        </div>
                    </div> 
              </li>
              <li class="itema diangw" >
                  <div class="itemb">
                     <i class="iconfont icon-shujukushenji zitib"></i>
                     <div class="zhifub">
                         <span>积分抵扣</span>
                    </div> 
                  </div>
                 <div class="dingweiwe">
                    <div class="radio" > 
                            <label>
                                <input type="radio" name="sex" value="" />
                                <div class="option"></div><!--该div盛放的是优化后的按钮图片-->
                            
                            </label>
                        </div>
                    </div> 
              </li>       
            
          </ul>
      </div>
       <div class="btn">
        <p >立即缴纳</p>
    </div> 
  </div>
</template>
<script>
export default {
  name: 'Wuyejiaona',
      data () {
    return {
      msg: 'moban'
    }
  }
  
}
</script>
<style  scoped>
@import "Wuyejiaona.css";
</style>