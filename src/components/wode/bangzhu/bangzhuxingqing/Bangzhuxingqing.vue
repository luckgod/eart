<template>
  <div>
    <p style="font-size: 0.38rem;
    line-height: 1rem;
    text-indent: 0.4rem;">{{tit}}</p>

    <p v-html="qb" style="font-size:0.3rem;line-height: 0.5rem;padding:0.2rem"></p>
  </div>
</template>
<script>
import { Toast } from "mint-ui";
export default {
  name: "Bangzhuxingqing",
  data() {
    return {
      msg: "moban",

      qb: "",
      tit: ""
    };
  },
  methods: {
    weizhi() {
      var data = {
        helpCode: this.$route.query.id
      };
      this.dataApi.ajax("singleHelpCenter", data, res => {
        if (res.respState == "S") {
          console.log(res);
          this.tit = res.helpTitle;
          this.qb = res.helpContent;
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
</style>