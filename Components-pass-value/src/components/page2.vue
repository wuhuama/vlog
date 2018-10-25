<template>
    <div class="page2">
      <fieldset>
        <legend>组件二</legend>
        <p>
            <span>口袋一共总金额：{{totalMoney}}元 </span>剩余金额：
            <span>{{balance}}元</span>
        </p>
        <button @click="toPage1Data">点击传给组件一</button>
        <div class="from1">{{msg}}</div>
      </fieldset>
    </div>
</template>
<script>
// 引入公共的bug，来做为中间传达的工具
import bus from "../eventBus.js";
export default {
  data() {
    return {
      balance: 1000,
      totalMoney: 1000,
      msg: ''
    };
  },
  mounted() {
    // 用$on事件来接收参数
    bus.$on("priceChange", (price, count) => {
      this.balance = this.totalMoney - price * count;
    });
    console.log('parent:',this.$parent)

    bus.$on('sendPage2Data', (data) => {
      this.msg = data;
      console.log(data);
    })
  },
  methods :{
    toPage1Data () {
      bus.$emit('sendPage1Data', '我是组件二的数据')
    }
  }
};
</script>
<style scoped>
.page2{
  margin-top: 10px;
}
fieldset{
  border-color: blue
}
.from1 {
  color: red
}
</style>
