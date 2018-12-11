<template>
  <div>
    <div class="tit">
      <i class="iconfont icon-left zitia" @click="jumpa"></i>
      <i class="iconfont icon-fenxiang zitib" @click="fnx"></i>
    </div>
    <div>
      <div class="lunbo">
        <mt-swipe :auto="4000" style="width:100vw;height:5.6rem;">
          <mt-swipe-item v-for="(item,index) in lunbo" :key="index">
            <img :src="item.imageAddress" alt class="kimg">
          </mt-swipe-item>
        </mt-swipe>
      </div>
      <div class="se">
        <p class="proname">{{goodsName}}</p>
        <p class="projia">店铺价：¥{{goodsPrice}}</p>
        <p class="projifen">{{goodsIntegralPrice}}积分</p>
      </div>
      <div class="sea">
        <p class="proname">商品详情</p>
        <ul>
          <li v-for="(item,index) in xingqingtu" :key="index">
            <img :src="item.imageAddress" class="kimg" alt>
          </li>
        </ul>
      </div>
    </div>
    <div class="footera" v-if="goodsIntegralStock==0?true:false ">
      <p class="zuihoua">已售罄</p>
    </div>
    <div class="footer" @click="tanchaun" v-if="goodsIntegralStock!==0?true:false">
      <p class="zuihou">兑换</p>
    </div>
    <mt-popup v-model="popupVisible" style="border-radius:0.2rem; ">
      <div class="warp">
        <div class="tanc">
          <p class="tanct">提醒</p>
        </div>
        <div class="maisu">
          <p class="maisua">积分商品，需前往该门店自</p>
          <p class="maisua">行提货，是否进行兑换？</p>
        </div>
        <div class="btn">
          <span class="quxiao" @click="qux">取消</span>
          <span class="que" tag="span" @click="queding">确定</span>
        </div>
      </div>
    </mt-popup>
    <mt-popup v-model="popupVisibla" position="bottom">
      <div class="fenxiang">
        <div class="fenxiang_to">
          <ul>
            <li>
              <i class="iconfont icon-iconfontzhizuobiaozhunbduan32 zitiaa"></i>
              <span class="fenxiang_miao">微信好友</span>
            </li>
            <li>
              <i class="iconfont icon-weixinpengyouquan zitibb"></i>
              <span class="fenxiang_miao">微信朋友圈</span>
            </li>
            <li>
              <i class="iconfont icon-lianjie ziticc"></i>
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
export default {
  name: "Jfenduihuan",
  data() {
    return {
      msg: "moban",
      popupVisible: false,
      popupVisibla: false,
      lunbo: "",
      xingqingtu: "",
      goodsName: "",
      goodsPrice: "",
      goodsIntegralPrice: "",
      goodsIntegralStock: ""
    };
  },
  methods: {
    tanchaun() {
      //   this.$router.push({path:'/shangpinsousu'})
      this.popupVisible = true;
    },
    queding() {
      // to='duihuanjilu'

      var data = {
        orderType: "DG",
        distType: "ZT",
        payType: "GF",
        isIntegral: "Y",
        storeCode: "S0000000001",
        vos: {
          goodsCode: this.$route.query.id,
          goodsIsAsyn: "G",
          goodsBuyNum: "1"
        }
      };
      this.dataApi.ajax("addShopOrder", data, res => {
        if (res.respState == "S") {
          console.log(res);
          this.$router.push("duihuanjilu");
          // this.goodsName= res.goodsName
          // this.goodsPrice= res.goodsPrice
          // this.goodsIntegralPrice= res.goodsIntegralPrice
          // this.goodsIntegralStock= res.goodsIntegralStock

          //     this.lunbo=res.broadImages
          //     this.xingqingtu=res.detailImages
          //     this.qb=res.vos
        } else {
          Toast(res.respMsg);
        }
      });
    },
    qux() {
      this.popupVisible = false;
    },
    fnx() {
      this.popupVisibla = true;
    },
    fnxq() {
      this.popupVisibla = false;
    },
    jumpa() {
      this.$router.go(-1);
    },
    weizhi() {
      var data = {
        goodsCode: this.$route.query.id
      };
      this.dataApi.ajax("singleShopGoods", data, res => {
        if (res.respState == "S") {
          this.goodsName = res.goodsName;
          this.goodsPrice = res.goodsPrice;
          this.goodsIntegralPrice = res.goodsIntegralPrice;
          this.goodsIntegralStock = res.goodsIntegralStock;

          this.lunbo = res.broadImages;
          this.xingqingtu = res.detailImages;
          this.qb = res.vos;
        } else {
          Toast(res.respMsg);
        }
      });
    }
  },
  mounted: function() {
    this.weizhi();
  }
};
</script>
<style  scoped>
@import "Jfenduihuan.css";
</style>