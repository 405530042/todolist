<template>
  <div class="cross"></div>
</template>

<style lang="stylus" scoped>
.cross
        margin-left 324px
        top -34px
        cursor pointer
        width 15px
        height 15px !important
        border 1px solid rgb(123,123,123,0)
        border-radius 50%
        position relative
  &:before
        content '+'
        height 12px
        margin-left -2px
        transform rotate(360/8 deg)
        position absolute
        top -1px
        color rgb(123,123,123)
  &:hover
        border-color black
  &:hover&:before
        color black
</style>
