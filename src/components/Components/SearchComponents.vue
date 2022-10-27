<script setup>

const searchValue = defineEmits(["search", ""]);

function search() {
  searchValue("search", document.getElementById("search").value);
}

function reset() {
  searchValue("search", "");
  document.getElementById("search").value = "";
}

</script>

<template>
  <div>
    <input src="text" placeholder="请键入搜索" id="search" @input="search">
<!--    <button @click="search">搜索</button>-->
    <button @click="reset">清除搜索</button>
  </div>
</template>

<style scoped>
div {
  display: inline-block;
  position: absolute;
  left: 50%;
  transform: translateX(-50%);
}

input {
  width: 300px;
  height: 30px;
  border: 1px solid #ccc;
  border-radius: 5px;
  padding: 0 10px;
  box-sizing: border-box;
}

button {
  width: 100px;
  height: 30px;
  border: 1px solid #ccc;
  border-radius: 5px;
  margin-left: 10px;
  background-color: #fff;
  cursor: pointer;
}

button:hover {
  background-color: #ccc;
}

button:active {
  background-color: #aaa;
}

</style>