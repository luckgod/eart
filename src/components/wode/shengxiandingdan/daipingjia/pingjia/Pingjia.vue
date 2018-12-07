<template>
  <div>
    <div class="one_se"> 
        <div class="one_sele">
            <span>给我们打个分吧！</span>
        </div>
        <div  class="one_seri">
            
        <div id="app" class="row">
            <div class="form-group clearfix">
               
                <div class="col-md-8">
                    <div class="gradebox">
                        <img v-for="(star,index) in stars" v-bind:src="star.src" v-on:click="rating(index)" alt="星星图片" :key='index' />
                    </div>
                </div>
            </div>
        </div>
        </div>
       
    </div>
     <!-- <div class="twose">
            <textarea name="" id="" cols="30" rows="10" placeholder="分享你的购买心得">

            </textarea>
    </div> -->
    <div id="dynamic_create">
    <mt-field  v-model="dynamicContent" placeholder="发表您的动态" type="textarea" rows="4" ></mt-field>
    <div class="twose">
       
        <span  class="twose_b">注：最多只能上传5张图片哦～</span>
    </div>
    <uploader @getFiles='getImageList' @removeFiles='removeImage'></uploader>
    <!-- <div class="btn-wrapper">
        <mt-button class='btn-send' size="large" type="primary" @click="send">发布</mt-button>
    </div> -->
    
    <div class="three_se">
        <div  class="three_sea">
              <div class="dingwei">
                    <div class="radio" > 
                            <label>
                                <input type="checkbox" name="sex" v-model="niming" @click="danxun"/>
                                <div class="option"></div>
                            
                            </label>
              </div>
                        </div>
        </div>
        <div  class="three_seb">
            <span>匿名</span>
        </div>
        <div  class="three_sec">
            <span @click="submit">提交评价</span>
        </div>
    </div>
    
  
  </div>
  </div>
</template>
<script>
import bo from "../../../../../assets/bolunan.png"
import boa from "../../../../../assets/boluu.png"
import { Indicator, Toast } from "mint-ui";
import uploader from "./Upload";

var starOffImg = bo;
var starOnImg = boa;


export default {
  name: 'Pingjia',
      data () {
    return {
      msg: 'moban',
      stars: [{
                            src: starOffImg,
                            active: true
                        }, {
                            src: starOffImg,
                            active: true
                        }, {
                            src: starOffImg,
                            active: true
                        },
                        {
                            src: starOffImg,
                            active: true
                        }, {
                            src: starOffImg,
                            active: true
                        }
                    ],
                    starNum: 0,
                    dynamicContent: "", //动态内容
                    imgList: [], //已上传的图片集合
                    FilecodeList: [],
                    isSubmit: false,
                    niming:false,
                    data:{
                        orderCode:'',
                        evaluateType:'D',
                        evaluateIdent:'D',
                        isAnonymous:'',
                        evaluateStar:'',
                        evaluateContent:'',
                        vegetImageVos:[],
                    }
              
    
  }
},
        methods: {
                    //评分
                    rating: function(index) {
                        var total = this.stars.length; //星星总数
                        var idx = index + 1; //这代表选的第idx颗星-也代表应该显示的星星数量

                        //进入if说明页面为初始状态
                        if(this.starNum == 0) {
                            this.starNum = idx;
                            for(var i = 0; i < idx; i++) {
                                this.stars[i].src = starOnImg;
                                this.stars[i].active = true;
                            }
                        } else {
                            //如果再次点击当前选中的星级-仅取消掉当前星级，保留之前的。
                            if(idx == this.starNum) {
                                for(var i = index; i < total; i++) {
                                    this.stars[i].src = starOffImg;
                                    this.stars[i].active = false;
                                }
                            }
                            //如果小于当前最高星级，则直接保留当前星级
                            if(idx < this.starNum) {
                                for(var i = idx; i < this.starNum; i++) {
                                    this.stars[i].src = starOffImg;
                                    this.stars[i].active = false;
                                }
                            }
                            //如果大于当前星级，则直接选到该星级
                            if(idx > this.starNum) {
                                for(var i = 0; i < idx; i++) {
                                    this.stars[i].src = starOnImg;
                                    this.stars[i].active = true;
                                }
                            }

                            var count = 0; //计数器-统计当前有几颗星
                            for(var i = 0; i < total; i++) {
                                if(this.stars[i].active) {
                                    count++;
                                }
                            }
                            this.starNum = count;
                            
                        }
                    },
                     getImageList(files) {
      this.$nextTick(() => {
        for (let i = 0, len = files.length; i < len; i++) {
          this.imgList.push(files[i]);
          //上传图片
          //   this._getFileCode({
          //     Base64Str: files[i].src.split("base64,")[1],
          //     AttachmentType: this.$enums.AttachmentType.Activity
          //   });
        }
      });
    
    },
    //删除图片
    removeImage(index) {
      this.imgList.splice(index, 1);
    },

    //上传图片获取fileCode (目前该方法没调用，供参考)
    _getFileCode(obj) {
      // Indicator.open(this.lang.dynamic_publishing);
      this.$http
        .post(this.$profileApi.Shared_UploadImage, obj)
        .then(data => {
          if (data.Rstatus) {
            this.FilecodeList.push(data.Rdata);
          } else {
            // Toast(this.lang.dynamic_upload_fail);
          }
        })
        .catch(err => {
          //   Toast(this.lang.dynamic.dynamic_net_error);
        });
    },

    //创建动态 (发布动态的请求)
    createDynamic(arr) {
      this.isSubmit = true;
      this.$http
        .post(this.$profileApi.Dynamic_CreateDynamic, {
          Subject: this.dynamicContent,
          Files: arr
        })
        .then(data => {
          this.isSubmit = false;
          if (data.Rstatus) {
            // Toast(this.lang.dynamic_publish_ok);
            this.$router.back();
          } else {
            // Toast(this.lang.dynamic_publish_fail);
          }
        })
        .catch(err => {
          //   Toast(this.lang.dynamic_net_error);
        });
    },
    danxun(){
        console.log(this.niming)        
    },

    //发布事件
    send() {
    //  console.log(this.dynamicContent)
  
        //  this.data.vegetImageVos =this.imgList
         this.weizhi()
    //   Toast("提交信息在控制台里～图片地址是压缩后的base64地址");
    //   console.log("内容" + this.dynamicContent);
    //   console.log(this.imgList);

        if (this.dynamicContent.trim() == "" && this.imgList.length === 0) {
          // Toast(this.lang.dynamic_content_no_null);
          return;
        }
        //当图片还没上传成功
        let self = this;
        var timer = setInterval(function() {
          if (
            self.FilecodeList &&
            self.imgList &&
            self.FilecodeList.length < self.imgList.length
          ) {
            // Indicator.open(self.lang.dynamic_uploading)
            self.isSubmit = true;
          } else {
            clearInterval(timer);
            // Indicator.close();
            self.createDynamic(self.FilecodeList);
          }
        }, 200);


       
    },
    submit(){
      if(this.imgList.length>0){
           for (let index = 0; index < this.imgList.length; index++) {
                this.upload(this.imgList[index].file);
            }
        }else{
            this.weizhi();
        }
    },
    weizhi(){
        this.data.orderCode =this.$route.query.id
        this.data.evaluateStar =this.starNum+''

        this.data.isAnonymous =this.niming

         this.data.evaluateContent =this.dynamicContent
        this.dataApi.ajax('addEvaluate',this.data,res=>{
         
                    if(res.respState=='S'){
                        console.log(res)
                        
                        
                         this.qb=res.vos
                    }else{
                         Toast(res.respMsg);
                    }
                    
           
                })
    },
    upload(f){
        this.dataApi.upload('upload',f,res=>{
             if(res.respState=='S'){
                this.data.vegetImageVos.push(res.localPath);
             }
             if(this.data.vegetImageVos.length==this.imgList.length){
                 console.log('aaa')
                 var arr=[];
                 for (let index = 0; index < this.data.vegetImageVos.length; index++) {
                     arr = {
                          imageAddress:this.data.vegetImageVos[index],
                          imageSort:index
                     };
                     this.data.vegetImageVos=arr;
                 }
                 this.weizhi();
             }
        })
    }
                },
     components: {
    uploader
  },
   mounted:function(){
     
     
    
    
  },
  

}
</script>
<style  scoped>
@import "Pingjia.css";
</style>
<style lang="less" scoped>
//发布动态
#dynamic_create {
  height: 100vh;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  background: #fff;
}
#dynamic_create canvas {
  background: #000 !important;
}
.btn-send {
  margin: 22px;
  display: block;
  width: 100%;
}
.btn-wrapper {
  display: flex;
}
#dynamic_create .mint-cell {
  border: none;
}
</style>