<template>
  <div class="content">
    <login
      v-if="face"
      @delieve-email="getEmail"
      @delieve-phone="getPhone"
    >
    </login>
    <component
      :is="area"
      :account2="account"
      @submit="getData">
    </component>
  </div>
</template>

<style lang="stylus" scoped>
*
    font-family '微軟正黑體'
.content
    width 100%
    display inline-block
    justify-content center
</style>

<script>
import Login from '@/components/signup/Login.vue';
import Email from '@/components/signup/email.vue';
import Phone from '@/components/signup/phone.vue';

export default {
  components: {
    Login,
    Email,
    Phone,
  },
  data() {
    return {
      account: '',
      area: '',
      face: true,
      name: '',
      password: '',
    };
  },
  methods: {
    getEmail(msg) {
      this.account = msg;
      this.area = 'email';
      this.face = false;
    },
    getPhone(msg) {
      this.account = msg;
      this.area = 'phone';
      this.face = false;
    },
    getData(msg, msg2) {
      this.name = msg;
      this.password = msg2;
      this.$router.push('login');
    }
  }

};
</script>


