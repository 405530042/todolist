<template>
  <div class="content">
    <Headi></Headi>
    <Login></Login>
    <Foot></Foot>
  </div>
</template>


<style lang="stylus" scoped>
.content
    width 100%
    display inline-block
    justify-content center
    height auto
</style>

<script>

import Headi from '@/components/login/Headi.vue';
import Foot from '@/components/login/Foot.vue';
import Login from '@/components/login/Login.vue';

export default {
  components: {
    Headi,
    Foot,
    Login
  },
  data: function() {
    return {
      account: '',
      pas: '',
      type: 'password',
      error: 0,
      errorpas: 0,
      color: 'black',
      tabindex: '',
    };
  },
  methods: {
    check: function() {
      window.location('#/todo');
    },
    pasttype() {
      this.type = ((this.type === 'text') ? 'password' : 'text');
      this.color = ((this.color === 'black') ? 'aqua' : 'black');
    },
    hide() {
      this.error = '0';
      this.errorpas = '0';
    },
    clear() {
      this.account = '';
    }
  },
};
</script>

