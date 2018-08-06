<template>
  <form @submit.prevent="check">
    <div class="inputbox">
      <div style="padding-left:4px">
        <input
          v-model="account"
          placeholder="信箱/手機號碼"
          required>
        <cross @click.native="clear"></cross>
      </div>
    </div>
    <div class="inputbox">
      <div style="padding-left:17px">
        <input
          :type="type"
          v-model="pas"
          placeholder="密碼"
          required>

      </div>
      <eye
        :style="{borderColor:color}"
        @click.native="pastType"></eye>
    </div>
    <div class="inputbox">
      <div
        class="fixbox"
        style="border-bottom:1px solid #d9d9d9;">
        <button style="width:340px;height:38px;border-radius: 4px;background-color:#3DA8F5;color:#fff">登入</button>
      </div>
    </div>
  </form>
</template>

<style lang="stylus" scoped>
.inputbox
    display flex
    justify-content center
    height 50px
    margin 5% 0
  input
    width 340px
    height 38px
    border 1px solid gray
    border-radius 4px
    padding 6px
</style>



<script>

import Eye from '@/components/login/Eye.vue';
import Cross from '@/components/login/Cross.vue';

export default {
  components: {
    Eye,
    Cross
  },
  data() {
    return {
      account: '',
      pas: '',
      type: 'password',
      color: '',
    };
  },
  methods: {
    check() {
      this.$router.push('todo');
    },
    clear() {
      this.account = '';
    },
    pastType() {
      this.type = (this.type === 'text') ? 'password' : 'text';
    }
  },
};
</script>
