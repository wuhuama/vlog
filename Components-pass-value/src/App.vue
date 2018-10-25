<template>
  <div id="app">
    <p>单价: <input type="text" v-model="price"></p>
    <page1 :price="price" @downPricea="downPrice" ref="page1"></page1>
    <page2></page2>
  </div>
</template>

<script>
import Page1 from "./components/page1";
import Page2 from "./components/page2";
export default {
  name: "App",
  data() {
    return {
      price: ""
    };
  },
  components: {
    Page1,
    Page2
  },
  methods: {
    downPrice() {
      this.price = (this.price - 1).toString();
      console.log(this.$refs.page1)
    }
  }
};
</script>

