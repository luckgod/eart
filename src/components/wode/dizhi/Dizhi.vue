<template>
  <div>
      <div class="warp">
          <div v-for="(item,index) in qb" :key="index">
            <ul class="lcard">
                <li class="itema"><span>{{item.addressTakeName}}</span><span>{{item.addressTakeMobile}}</span></li>
                <li class="itemb"><span>{{item.addressProvName}} {{item.addressCityName}} {{item.addressAreaName}} {{item.addressTakeRoomName}}</span></li>
                <li class="itemc">
                    <div class="dingwei">
                    <div class="radio" > 
                            <label>
                                <input type="radio" name="sex" value="" />
                                <div class="option"></div><!--该div盛放的是优化后的按钮图片-->
                            
                            </label>
                        </div>
                    </div> 
                    <span>默认地址</span>
                    <span>编辑</span>
                    <span>删除</span>
                </li>
            </ul>
        </div>
       
         <div class="btn" @click="juam">
                <p >新增收货地址</p>
        </div>
      </div>
  </div>
</template>
<script>
export default {
  name: 'Dizhi',
      data () {
    return {
      msg: 'moban',
       data:{
        pageNum:1,
        pageSize:5,
        userCode:'0000000011',
      },
      data:{
        addressCode:1,
       
      },

      qb:'',
    }
  },
  methods:{
      juam(){
           this.$router.push({path:'/Xinzhengshouhuodizhi'})
      },
      weizhi(){
        this.dataApi.ajax('pageAddress',this.data,res=>{
                        console.log('111')
                    if(res.respState=='S'){
                        console.log(res)
                         this.qb=res.vos
                    }else{
                         Toast(res.respMsg);
                    } 
                })
    },
    del(){
        this.dataApi.ajax('delAddress',this.date,res=>{
                        
                    if(res.respState=='S'){
                        console.log(res)
                         this.qb=res.vos
                    }else{
                         Toast(res.respMsg);
                    } 
                })
    }
  },
  mounted:function(){
     this.weizhi()
  },
  
}
</script>
<style  scoped>
@import "Dizhi.css";
</style>