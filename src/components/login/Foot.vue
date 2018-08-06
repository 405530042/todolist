<template>
  <div
    class="inputbox"
    style="margin:0">
    <div class="fixbox">
      <span>
        <a href="#">第三方帳號登入</a>
      </span>
      <span>还没有帐号？
        <router-link to="signup">註冊新帳號</router-link>
      </span>
      <span>中国服务器</span>
    </div>
  </div>
</template>

<style lang="stylus" scoped>
.fixbox
    margin 0 !important
    margin-bottom  12px
    height 60px
    text-align center
    display grid 
  span
    margin 1px 0

a
    text-decoration none
    color #03a9f4 !important
    font-size 14px
 a&:hover
    color #3da8f5 !important
</style>

