<template>
  <div class="head-content">
    <div class="header">
      <div class="headimg">
        <img src="@/image/xiao.jpg">
      </div>
      <div class="headimg">
        <img src="@/image/teambition.png">
      </div>
      <div class="headimg">
        <img src="@/image/xiao.jpg">
      </div>
    </div>
    <div class="nav">
      <div class="nav-item">
        <img src="@/image/xiao.jpg">
      </div>
      <div class="nav-item">
        <ul>
          <li>任務</li>
        </ul>
      </div>
      <div class="nav-item">
        <img src="@/image/xiao.jpg">
      </div>
    </div>
  </div>
</template>
<style lang="stylus" scoped>
.header {
    width: 100%;
    height: 48px;
    display: flex;
    justify-content: space-between;
    z-index: 100;
    border-bottom: 2px solid #d9d9d9;
}

.headimg {
    height: 100%;
    display: flex;
    align-items: center;
}

.headimg img {
    height: 29.2%;
}

.nav {
    background-color: #f5f5f5;
    width: 100%;
    height: 48px;
    display: flex;
    justify-content: space-between;
    position: fixed;
    border-bottom: 1px solid #d9d9d9;
}

.nav-item {
    height: 100%;
    text-align: center;
    display: flex;
}

.nav-item ul {
    list-style-type: none;
    display: flex;
    padding: 0;
}

.nav-item li {
    font-size: 1.2em;
    font-weight: 900;
    display: flex;
    align-items: center;
}

.nav-item img {
    height: 100%;
}

.head-content
    width 100%
</style>

