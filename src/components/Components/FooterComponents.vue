<script setup>

</script>

<template>
  <div id="root">
    <div id="text">
      网站底部/网站底部/网站底部/网站底部/网站底部/网站底部
    </div>
    <div id="login">
      会员登录
    </div>
    <div id="register">
      会员注册
    </div>
  </div>
</template>

<style scoped>

#root {
  /*  定位到底部*/
  position: fixed;
  bottom: 0;
  width: 100%;
  height: 50px;
  background-color: #809eff;
  display: flex;
  justify-content: right;
  align-items: center;
}

div {
  display: flex;
  align-items: center;
}

#text,
#login,
#register {
  margin: 5px 5px;
  color: white;
  user-select:none;
}

#login {
  background-color: greenyellow;
}

#register {
  background-color: red;
}

</style>