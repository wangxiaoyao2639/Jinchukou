<template>
  <div class="left-indicator">
    <div v-for="item in data" :key="item.key" class="single-indicator">
      <img class="huan-img" :src="Huan" alt />
      <img class="huan-icon" :src="Icon1" alt />
      <div class="right">
        <div class="title">{{item.name}}</div>
        <div class="value-num">{{item.value}}</div>
        <span class="unit">亿</span>
        <div class="value-num">{{item.num}}</div>
        <span class="unit">笔</span>
      </div>
    </div>
  </div>
</template>

<script>
import huan from "../../assets/images/Untitled-huan1.png";
import icon5 from "../../assets/images/jinchukou/icon05.png";
import icon1 from "../../assets/images/jinchukou/icon01.png";
export default {
  name: "",
  props: [],
  mounted() {},
  data() {
    return {
      Huan: huan,
      Icon5: icon5,
      Icon1: icon1,
      data: [
        {
          name: "贷款发放",
          value: "1,620.13",
          key: "dai1",
          num: "234"
        },
        {
          name: "贷款签约",
          value: "1,620.13",
          key: "lei1",
          num: "124"
        }
      ]
    };
  },
  computed: {},
  methods: {},
  components: {}
};
</script>

<style lang="less" scoped>
.left-indicator {
  .single-indicator {
    position: relative;
    height: 112px;
    width: 100%;
    margin-bottom: 46px;
    .huan-img {
      margin-right: 34px;
      display: inline-block;
      width: 110px;
      height: 108px;
      vertical-align: top;
    }
    .huan-icon {
      position: absolute;
      top: 30px;
      left: 30px;
      width: 48px;
      height: 48px;
    }
    .right {
      display: inline-block;
      .title {
        color: rgba(255, 255, 255, 1);
        font-family: Microsoft YaHei;
        font-weight: regular;
        font-size: 32px;
        line-height: normal;
        letter-spacing: 0px;
        text-align: left;
      }
      .value {
        color: rgba(255, 166, 101, 1);
        font-family: Microsoft YaHei;
        font-weight: bold;
        font-size: 28px;
        line-height: normal;
        letter-spacing: 0px;
        text-align: left;
      }
      .value-num {
        display: inline-block;
        margin-right: 24px;
        color: #fff;
        font-family: Microsoft YaHei;
        font-weight: bold;
        font-size: 56px;
        line-height: normal;
        letter-spacing: 0px;
        text-align: left;
      }
      .unit {
        display: inline-block;
        color: rgba(255, 255, 255, 1);
        font-family: Microsoft YaHei;
        font-weight: regular;
        font-size: 32px;
        line-height: normal;
        letter-spacing: 0px;
        text-align: left;
        margin-right: 70px;
      }
    }
  }
}
</style>
