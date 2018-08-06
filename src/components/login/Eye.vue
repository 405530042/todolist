<template>
  <div class="eyeicon"></div>
</template>


<style lang="stylus" scoped>
.eyeicon
    z-index 100
    opacity 0.5
    border 2px solid
    border-color black
    width 13px
    height 13px
    top 17.97px
    left -30px
    border-radius 75% 15%
    position relative
    transform rotate(360/8 deg)
  &:before
    content ''
    display block
    position absolute
    width 7px
    height 7px
    border-color black
    border-radius 50%
    left 3px
    top 3px
    background-color black
  &:hover
    cursor pointer
    opacity 1
</style>
