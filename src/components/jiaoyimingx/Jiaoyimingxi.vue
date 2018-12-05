<template>
  <div>
      <div>
          <ul>
              <li class="item" v-for="(item,index) in qb">
                  <ul class="itema">
                      <li class="fll itemb">
                          <p class="iname " >{{item.changeRemark}}</p>
                          <span  class="itime ">{{item.creTime}}</span>
                        </li>
                      <li  class="flr"><span class="itimepro" :class="item.changeDirection=='A'?'yanse':''" >{{item.changeDirection=='D'?'-':''}} {{item.changeValue}}积分</span></li>
                  </ul>
              </li>
              
          </ul>
      </div>
      <div class="tip">
          <p class="quan">已显示全部</p>   
      </div>
  </div>
</template>
<script>
export default {
  name: 'Jiaoyimingxi',
      data () {
    return {
      msg: 'moban',
      num:50,
      data:{
        pageNum:1,
        pageSize:5,
        userCode:'0000000011',
        userWealthType:'G',
        userWealthIdent:'D',
      },
      qb:'',
    }

  },
   methods:{
      weizhi(){
       
        this.dataApi.ajax('pageUserWealth',this.data,res=>{
          console.log('111')
                    if(res.respState=='S'){
                        console.log(res)
                        
                        
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
@import "Jiaoyimingxi.css";
</style>