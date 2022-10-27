<script setup>

import {ref} from "vue";

import filterList from "../Data/filterList.json";
import commodityData from "../Data/commodityData.json";
import advertisement from "../Data/advertisement.json";

import Linq from "linq";

const listBool = ref([false, false, false]);
const type = ref(0);

const props = defineProps({
  searchValue: String
})

//展开或收起
function changeListBool(index) {
  listBool.value[index] = !listBool.value[index];
}

//更改筛选条件
function changeType(typeIndex) {
  if (typeIndex === type.value) {
    type.value = 0;
  } else {
    type.value = typeIndex;
  }
}

//模糊搜索
function search(str) {
  if (str.length === 0) {
    return commodityData;
  } else {
    type.value = 0;
    return Linq.from(commodityData)
        .where(item => {
          for (let i = 0; i < item.name.length; i++) {
            if (item.name.indexOf(str) !== -1) {
              return item.name[i];
            }
          }
        }).toArray();
  }
}


</script>

<template>
  <div id="root">
    <!--  左侧筛选器-->
    <div id="typeChoose">
      <div v-for="item in filterList" :key="item">
        <div @click="changeListBool(filterList.indexOf(item))" id="title">{{ item.title }}</div>
        <div v-if="listBool[filterList.indexOf(item)]">
          <div v-for="item2 in item.data" :key="item2" id="data" @click="changeType(item2.type)"
               v-bind:class="{data2:item2.type===type}">
            {{ item2.name }}
          </div>
        </div>
      </div>
    </div>

    <!--  中间商品列表-->
    <div id="goodsList">
      <div v-for="item in search(props.searchValue)" :key="item">
        <div id="goods" v-if="type===item.type||type===0">
          <img :src="item.img" alt="" id="commodityImg">
          <div id="price">￥{{ item.price }}</div>
          <div id="name">{{ item.name }}</div>
        </div>
      </div>
    </div>

    <!--    右侧广告位-->
    <div id="advertisementList">
      <a v-for="item in advertisement" :key="item" :href="item.url" target="_blank" id="advertisementItem">
        <img :src="item.img" alt="AD" id="AdImg">
      </a>
      <video controls autoplay id="AdVideo">
        <source src="http://clips.vorwaerts-gmbh.de/big_buck_bunny.mp4" type="video/mp4">
      </video>
    </div>

  </div>

</template>

<style scoped>

#goodsList {
  display: flex;
  flex-wrap: wrap;
  max-width: 880px;
  margin: 0 auto;
}

#goods {
  display: inline-block;
  float: left;
  width: 200px;
  height: auto;
  margin: 10px;
  border: 1px solid #ccc;
  border-radius: 5px;
  padding: 10px;
  box-sizing: border-box;
  text-align: center;
}

#typeChoose {
  position: absolute;
  max-width: 200px;
  margin-left: 1%;
  cursor: pointer;
}

#advertisementList {
  position: absolute;
  right: 1%;
}

#advertisementList,
#AdImg,
#AdVideo {
  width: 200px;
}

#commodityImg {
  width: 100%;
  height: 100%;
}

#root {
  display: flex;
  margin-top: 20px;
}

#title, #data {
  display: flex;
  font-size: 20px;
  margin: 5px 0;
}

#title {
  color: #809eff;
  width: 200px;
  user-select: none;
}


#data {
  margin: 0 30px;
  user-select: none;
}

.data2 {
  color: #809eff;
}

</style>