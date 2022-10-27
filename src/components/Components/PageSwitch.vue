<script setup>

import {ref} from "vue";

const emit = defineEmits(["num", ""]);

const page = ref(0);

function setIndex(i) {
  emit("num", i);
  page.value = i;
}

</script>

<template>
  <div id="root">
    <div id="btn" v-bind:class="{switchBtn:page===0}" @click="setIndex(0)">首页</div>
    <div id="btn" v-bind:class="{switchBtn:page===1}" @click="setIndex(1)">商品详情</div>
    <div id="btn" v-bind:class="{switchBtn:page===2}" @click="setIndex(2)">购物车</div>
    <div id="btn" v-bind:class="{switchBtn:page===3}" @click="setIndex(3)">我的订单</div>
  </div>
</template>

<style scoped>

#root {
  display: flex;
  /*justify-content: space-around;*/
  background-color: #cccccc;
  height: 50px;
}

#btn {
  flex: 1;
  display: flex;
  justify-content: center;
  align-items: center;
  cursor: pointer;
  color: white;
}

.switchBtn {
  background-color: #809eff;
}

</style>