<template>
  <div>
    <div class="shangpinxiangqing">
      <mt-swipe :auto="4000" class="lunbo_two" :show-indicators="false">
        <mt-swipe-item class="lunboli_two" v-for="(item,index) in broadImages" :key="index">
          <img :src="item.imageAddress" alt>
        </mt-swipe-item>
      </mt-swipe>

      <i class="iconfont icon-left fanhui" @click="fanhu"></i>
    </div>
    <div class="miaosh-he">
      <span>限量特价中</span>
      <span class="miaosh_her">距结束</span>
      <div class="shijian">
        <span class="shijiana">02</span>
        <span>:</span>
        <span class="shijiana">02</span>
        <span>:</span>
        <span class="shijiana">02</span>
      </div>
    </div>
    <div class="shangpinxiangqing_three">
      <ul>
        <li class="shangpinxiangqing_three_name">
          <span>{{goodsName}}</span>
        </li>
        <li class="shangpinxiangqing_three_jianjie">
          <span>{{goodsExplain}}</span>
        </li>
        <li class="shangpinxiangqing_three_jiage">
          <span>¥{{goodsActivityPrice}}</span>
          <span v-if='goodsIsActivity=='N'?'':'''></span>
          <span>¥{{goodsPrice}}</span>
          <span>已售{{goodsClicks}}</span>
        </li>
      </ul>
      <i class="iconfont icon-fenxiang gouwu" @click="fnx"></i>
    </div>
    <div class="tuijianshangpin">
      <div class="tuijianshangpin-tit">
        <span>推荐商品</span>
      </div>
      <div class="miaosha_pro">
        <ul class="slide-box">
          <li class="slide-box-oli">
            <div class="slide-box-oimg">
              <img src="../../../assets/logo.png" alt>
            </div>
            <div class="slide-box-na">赣南高级脐橙2个</div>
            <div class="slide-box-sho">
              <span class="fll">¥8.80</span>
              <i class="iconfont icon-gouwuche flr"></i>
            </div>
          </li>
          <li class="slide-box-oli">
            <div class="slide-box-oimg">
              <img src="../../../assets/logo.png" alt>
            </div>
            <div class="slide-box-na">赣南高级脐橙2个</div>
            <div class="slide-box-sho">
              <span class="fll">¥8.80</span>
              <i class="iconfont icon-gouwuche flr"></i>
            </div>
          </li>
          <li class="slide-box-oli">
            <div class="slide-box-oimg">
              <img src="../../../assets/logo.png" alt>
            </div>
            <div class="slide-box-na">赣南高级脐橙2个</div>
            <div class="slide-box-sho">
              <span class="fll">¥8.80</span>
              <i class="iconfont icon-gouwuche flr"></i>
            </div>
          </li>
          <li class="slide-box-oli">
            <div class="slide-box-oimg">
              <img src="../../../assets/logo.png" alt>
            </div>
            <div class="slide-box-na">赣南高级脐橙2个</div>
            <div class="slide-box-sho">
              <span class="fll">¥8.80</span>
              <i class="iconfont icon-gouwuche flr"></i>
            </div>
          </li>
        </ul>
      </div>
    </div>
    <div class="shangpinxiangqing_four">
      <p>商品详情</p>
      <div class="shangpinxiangqing_four_img">
        <ul>
          <li v-for="(item,index) in detailImages" :key="index">
            <img :src="item.imageAddress" alt>
          </li>
        </ul>
      </div>
    </div>
    <div class="shangpinxiangqing_five">
      <span @click="kefu">
        <i class="iconfont icon-kefu1 zitifivk"></i>
      </span>
      <router-link to="shopcar" tag="span">
        <i class="iconfont icon-gouwuche zitifivc"></i>
        <div class="pronum">0</div>
      </router-link>
      <router-link to="querendingdan" tag="span">立即购买</router-link>
      <span>加入购物车</span>
    </div>
    <mt-popup v-model="popupVisible" position="bottom">
      <div class="fenxiang">
        <div class="fenxiang_to">
          <ul>
            <li>
              <i class="iconfont icon-iconfontzhizuobiaozhunbduan32 zitia"></i>
              <span class="fenxiang_miao">微信好友</span>
            </li>
            <li>
              <i class="iconfont icon-weixinpengyouquan zitib"></i>
              <span class="fenxiang_miao">微信朋友圈</span>
            </li>
            <li>
              <i class="iconfont icon-lianjie zitic"></i>
              <span class="fenxiang_miao">微信朋友圈</span>
            </li>
          </ul>
        </div>
        <div class="fenxiangbtn">
          <span @click="fnxq">取消</span>
        </div>
      </div>
    </mt-popup>
  </div>
</template>
<script>
import { MessageBox } from "mint-ui";
export default {
  name: "Qianggouxiangqing",
  data() {
    return {
      msg: "moban",
      popupVisible: false,
      data: {
        goodsCode: ""
      },
      broadImages: "",
      vegetAttributeVos: "",
      detailImages: "",
      goodsName:'',
      goodsExplain:'',
      goodsPrice:'',
      goodsActivityPrice:'',
      goodsIsActivity:'',
       // 商品单位
      goodsUnit:'',
      goodsClicks:'',
    };
  },
  methods: {
    fnx() {
      this.popupVisible = true;
    },
    fnxq() {
      this.popupVisible = false;
    },
    kefu() {
      MessageBox({
        title: "",
        message: "1234687879879?",
        showCancelButton: true
      });
    },
    fanhu() {
      this.$router.go(-1);
    },
    fatdata() {
      // console.log(this.$route.query.id)
      this.data.goodsCode = this.$route.query.id;
      this.dataApi.ajax("singleShopGoods", this.data, res => {
        if (res.respState == "S") {
          console.log(res);
          this.broadImages = res.broadImages;
        this.detailImages=res.detailImages
        this.goodsName=res.goodsName
        this.goodsExplain=res.goodsExplain
        this.goodsPrice=res.goodsPrice
        this.goodsActivityPrice=res.goodsActivityPrice
        this.goodsIsActivity=res.goodsIsActivity
        this.goodsUnit=res.goodsUnit
        this.goodsClicks=res.goodsClicks
        
          console.log(this.detailImages);
        }
      });
    }
  },
  mounted() {
    this.fatdata();
  }
};
</script>
<style  scoped>
@import "Qianggouxiangqing.css";
</style>