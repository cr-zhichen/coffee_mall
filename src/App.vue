<script setup>
import {ref} from "vue";

import BannerAdvertis from './components/Components/BannerAdvertis.vue'
import LogoComponents from './components/Components/LogoComponents.vue'
import SearchComponents from './components/Components/SearchComponents.vue'
import PageSwitch from './components/Components/PageSwitch.vue'
import FooterComponents from './components/Components/FooterComponents.vue'
import HomePageComponents from './components/Page/HomePageComponents.vue'

const page = ref(0);
const searchValue = ref("");


</script>


<template>

  <!-- Banner图 -->
  <BannerAdvertis></BannerAdvertis>

  <!-- Logo和搜索框 -->
  <div id="title">
    <LogoComponents></LogoComponents>
    <SearchComponents @search="(msg) => searchValue = msg"></SearchComponents>
  </div>

  <!-- 页面选择 -->
  <PageSwitch @num="(msg) => page = msg"></PageSwitch>

  <!-- TODO 主页面-->
  <div id="page">
    <HomePageComponents v-if="page === 0" :searchValue="searchValue"></HomePageComponents>
  </div>

  <!-- 页脚-->
  <FooterComponents></FooterComponents>

</template>


<style>
#title {
  display: flex;
  align-items: center;
}

#page {
  margin-bottom: 50px;
}
</style>
