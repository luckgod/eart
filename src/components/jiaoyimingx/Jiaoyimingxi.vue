<template>
  <div>
      <div>
          <ul>
<<<<<<< HEAD
              <li class="item" v-for="(item,index) in qb">
                  <ul class="itema">
                      <li class="fll itemb">
                          <p class="iname " >{{item.changeRemark}}</p>
                          <span  class="itime ">{{item.creTime}}</span>
                        </li>
                      <li  class="flr"><span class="itimepro" :class="item.changeDirection=='A'?'yanse':''" >{{item.changeDirection=='D'?'-':''}} {{item.changeValue}}积分</span></li>
                  </ul>
              </li>
              
=======
              <li class="item" >
                  <ul class="itema">
                      <li class="fll itemb">
                          <p class="iname " >租田套餐</p>
                          <span  class="itime ">2018-04-28 17:00:04</span>
                        </li>
                      <li  class="flr"><span class="itimepro">-2880积分</span></li>
                  </ul>
              </li>
              <li class="item" >
                  <ul class="itema">
                      <li class="fll itemb">
                          <p class="iname " >生鲜订单</p>
                          <span  class="itime ">2018-04-28 17:00:04</span>
                        </li>
                      <li  class="flr"><span class="itimepro" :class=" num > 0 ? 'yanse' : '' ">{{num}}积分</span></li>
                  </ul>
              </li>
              <li class="item" >
                  <ul class="itema">
                      <li class="fll itemb">
                          <p class="iname " >生鲜退款</p>
                          <span  class="itime ">2018-04-28 17:00:04</span>
                        </li>
                      <li  class="flr"><span class="itimepro">-50积分</span></li>
                  </ul>
              </li>
              <li class="item" >
                  <ul class="itema">
                      <li class="fll itemb">
                          <p class="iname " >农田订单</p>
                          <span  class="itime ">2018-04-28 17:00:04</span>
                        </li>
                      <li  class="flr"><span class="itimepro">-2880积分</span></li>
                  </ul>
              </li>
>>>>>>> cd32d3b470d2fe7eb757becad960d935fdd46f19
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
<<<<<<< HEAD
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
=======
    }
  }
>>>>>>> cd32d3b470d2fe7eb757becad960d935fdd46f19
  
}
</script>
<style  scoped>
@import "Jiaoyimingxi.css";
</style>