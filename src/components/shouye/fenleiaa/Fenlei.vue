<template>
  <div>
    <div class="dingwei">
     <div class="serash">
       <input type="text" placeholder="输入商品名称">
     </div>
     </div>
     <div class="liebiao">
       <ul>
         <li v-for="(list,index) in qb" class="nav" :class="{ red:changeRed == index}" @click.stop="reds(index)" :key='index'>{{list.cateName}}</li>
         
       </ul>
     </div>
     <div class="shju">
       <div class="shjutu">
         <img :src="fengmiantu">
       </div>
      <div class="slide-box">
           <div v-for="(list,index) in qe" class="slide-item" :class="{ red:changeReda == index}" @click.stop="redsa(index)" :key='index'>{{list.cateName}}</div>
       
    </div>
     <div>
        <div class="proa">
        <ul class="proaoul" v-for="(item,index) in qt" :key="index">
            <!-- style="border:1px solid black" -->
            <li class="proaoula"><img :src="item.goodsIcon" alt="" class="proaomg"></li>
            <li class="proaoulb">
                <ul>
                    <li class="proatit"><span >{{item.goodsName}}</span></li>
                    <li class="proayishou"><span >{{item.goodsExplain}}</span></li>
                    <li class="proaqian"><span >¥{{item.goodsIsActivity=='Y'?item.goodsActivityPrice:item.goodsPrice}}/份</span><i class="iconfont icon-gouwuche ziti"></i></li>
                </ul>
            </li>
        </ul>
    </div>
    
    
    
    
    
   
   
   
  </div>
  </div>
   </div>
</template>
<script>
export default {
  name: 'Fenlei',
      data () {
    return {
      msg: 'Fenlei',

                changeRed:0,
               
                changeReda:0,
                yiji:0,
                erji:0,
                  data:{
                    selectType:'A',
                    cateParentCode:'#',
                    
                },
                 qb:'',
                 date:{
                        pageNum:1,
                        pageSize:10,
                        sort:'UPD_TIME',
                        desc:'ASC',
                        goodsState:'U',
                        goodsType:'S',
                        goodsOneCate:0,
                        goodsTwoCate:0,
                        storeCode:'S0000000000',

                 },
                 qt:'',
                 qe:'',
                 fengmiantu:'',
            
    }
  },
  methods:{
            chaundi(e){
                console.log(e.target)
            },
            reds:function(index){
                    this.changeRed = index;
                    // console.log(index)
                    this.yiji=index
                    
                     
                    this.weizhi()
                    this.lieboa()
                    
                   
                    
                     
                     
                    
            },
            redsa:function(index){
                    this.changeReda = index;
                    this.erji=index
                   
                     this.weizhi()
                      this.lieboa()
            },
            weizhi(){
       
            this.dataApi.ajax('selectShopCate',this.data,res=>{
            // console.log('111')
                    if(res.respState=='S'){
                        //    console.log(res)
                         this.erji=0
                        this.date.goodsOneCate=res.vegetShopCateVos[this.yiji].cateCode
                        this.date.goodsTwoCate=res.vegetShopCateVos[this.yiji].childCate[this.erji].cateCode
                        
                        this.qb=res.vegetShopCateVos
                        this.qe=res.vegetShopCateVos[this.yiji].childCate
                        this.fengmiantu=res.vegetShopCateVos[this.yiji].cateIcon
                    }else{
                         Toast(res.respMsg);
                    }
                    
           
                })
            },
            lieboa(){
       
            this.dataApi.ajax('pageStoreGoods',this.date,res=>{
                // console.log('111')
                        if(res.respState=='S'){
                            console.log(res)
                            
                            
                            this.qt=res.vos
                        }else{
                            Toast(res.respMsg);
                        }
                        
            
                    })
            },


            },
            mounted:function(){
                
                this.weizhi()
                this.lieboa()
                
            },
  
}
</script>
<style  scoped>
@import "Fenlei.css";
</style>