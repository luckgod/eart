<template>
  <div>
      <div class="warp">
            <div class="biaodan">
                <ul>
                    <li class="item teshu">
                        <label for="a">收货人 </label>
                        <input type="text" placeholder="须与身份证一致" id="a">
                    </li>
                      <li class="item">
                        <label for="a">手机号码</label>
                        <input type="text" placeholder="请填写收件人手机号" id="a">
                    </li>
                      <li class="item">
                        <label for="a">所在地区</label>
                        <input type="text" placeholder="省市区" id="a" @click="popupVisible =!popupVisible" v-model="dizhi">
                        <div>
                          <mt-popup
                            v-model="popupVisible"
                            position="bottom"
                            style="width:100vw;">
                        　　<mt-picker :slots="myAddressSlots" @change="onMyAddressChange"></mt-picker>
                        　 </mt-popup>
                        </div>
                        </li>
                      <li class="item">
                        <label for="a">选择小区</label>
                        <input type="text" placeholder="该地区暂无小区" id="a">
                    </li>
                      <li class="item">
                        <label for="a">详细地址</label>
                        <input type="text" placeholder="请输入详细地址" id="a">
                    </li>
                      <li class="itema">
                          <span>设为默认地址</span>
                          <div class="dingwei">
                              <input class="switch switch-anim" type="checkbox" checked>
                          </div>
                      </li>
                </ul>
            </div> 
             <div class="btn">
                <p >保存</p>
              </div> 
      </div>
  </div>
</template>
<script>
import { Picker } from 'mint-ui';
import myaddress from './address3.json'
import { Popup } from 'mint-ui';
export default {
  name: 'Xinzhengshouhuodizhi',
  components: {
　　　　'mt-picker': Picker
　　},
      data () {
    return {
        msg: true,
        　isShowAddress:false,
          popupVisible:false,
　　　　　　myAddressSlots: [
　　　　　　　　{
　　　　　　　　　　flex: 1,
　　　　　　　　　　defaultIndex: 1,
　　　　　　　　　　values: Object.keys(myaddress), //省份数组
　　　　　　　　　　className: 'slot1',
　　　　　　　　　　textAlign: 'center'
　　　　　　　　}, {
　　　　　　　　　　divider: true,
　　　　　　　　　　content: '-',
　　　　　　　　　　className: 'slot2'
　　　　　　　　}, {
　　　　　　　　　　flex: 1,
　　　　　　　　　　values: [],
　　　　　　　　　　className: 'slot3',
　　　　　　　　　　textAlign: 'center'
　　　　　　　　},{
　　　　　　　　　　divider: true,
　　　　　　　　　　content: '-',
　　　　　　　　　　className: 'slot4'
　　　　　　　　},{
　　　　　　　　　　flex: 1,
　　　　　　　　　　values: [],
　　　　　　　　　　className: 'slot5',
　　　　　　　　　　textAlign: 'center'
　　　　　　　　}
　　　　　　],
　　　　myAddressProvince:'',
　　　　myAddressCity:'',
　　　　myAddresscounty:'',
　　　　dizhi:'',
        phone:'',
        diqu:'',
        xiaoqu:'',
        xidizhi:'',
        username:'',
        data:{
      
      },
      qb:'',
       date:{
      addressCode:'F423D4F13B054E6786BF7FB6795DD92C',
      }
    }
   
  },
  methods:{
      weizhi(){
       
        this.dataApi.ajax('selectTotalCity',this.data,res=>{
         
                    if(res.respState=='S'){
                        // console.log(res)
                        
                        
                         this.qb=res.vos
                    }else{
                         Toast(res.respMsg);
                    }
                    
           
                })
    },
    　goBack (){
　　　　　　this.$router.go(-1)
　　　　},
　　　　closeShowAddress (e){
　　　　　　if(e.target == this.$refs.selectAddress){
　　　　　　　　this.isShowAddress = !this.isShowAddress;
　　　　　　}
　　　　},
　　　　onMyAddressChange(picker, values) {
　　　　　　if(myaddress[values[0]]){ //这个判断类似于v-if的效果（可以不加，但是vue会报错，很不爽）
　　　　　　　　picker.setSlotValues(1,Object.keys(myaddress[values[0]])); // Object.keys()会返回一个数组，当前省的数组
　　　　　　　　picker.setSlotValues(2,myaddress[values[0]][values[1]]); // 区/县数据就是一个数组
　　　　　　　　this.myAddressProvince = values[0];
　　　　　　　　this.myAddressCity = values[1];
　　　　　　　　this.myAddresscounty = values[2];
              this.dizhi= values[0]+' '+ values[1]+' '+values[2]
　　　　　　}
　　　　},
      bianjidizhi(){
            this.dataApi.ajax('singleAddress',this.date,res=>{         
                     if(res.respState=='S'){
                         console.log(res)
                         // this.qb=res.vos
                     }else{
                          Toast(res.respMsg);
                     }
                 })
            // this.dataApi.ajax('editAddress',this.date,res=>{         
            //         if(res.respState=='S'){
            //             console.log(res)
            //             // this.qb=res.vos
            //         }else{
            //              Toast(res.respMsg);
            //         }
            //     })
      }
  },
  mounted:function(){
     
    //  this.weizhi()
//     this.$nextTick(() => { //vue里面全部加载好了再执行的函数 （类似于setTimeout）
// 　　　　　　this.myAddressSlots[0].defaultIndex = 0
// 　　　　　　// 这里的值需要和 data里面 defaultIndex 的值不一样才能够初始化
// 　　　　　　//因为我没有看过源码（我猜测是因为数据没有改变，不会触发更新）
// 　　　　});
    this.bianjidizhi()
  },
  
}
</script>
<style  scoped>
@import "Xinzhengshouhuodizhi.css";
</style>