<template>
  <div class="email-area">
    <headi></headi>
    <form @submit.prevent="submitData">
      <div class="sign">
        <div class="inputbox">
          <input
            v-model="account2"
            :placeholder="account2"
            class="sign-account"
            readonly
            disable>
        </div>
        <div class="inputbox">
          <input
            :value="name"
            class="input-name"
            placeholder="姓名"
            required
            @input="name=$event.target.value">
          <cross @click.native="clear"></cross>
        </div>
        <div class="inputbox pas">
          <input
            :type="pasType"
            :value="password"
            placeholder="密碼"
            required
            @input="password=$event.target.value">
          <eye @click.native="changeType"></eye>
        </div>
        <div class="inputbox pas">
          <input
            :type="pas2Type"
            :value="recheck"
            placeholder="確認新密碼"
            required
            @input="recheck=$event.target.value">
          <eye @click.native="changeType2"></eye>
        </div>
        <div class="inputbox">
          <div class="fixbox">
            <input
              class="submit-button"
              type="submit"
              value="註冊">
          </div>
        </div>
        <div class="inputbox">
          <div class="fixbox">
            <label class="check-label">
              <input
                type="checkbox"
                class="checkbox">我已同意
            </label>
          </div>
        </div>
      </div>
    </form>
  </div>
</template>
<style lang="stylus" scoped>
.sign-account
    background-color #b3b3b3
    cursor not-allowed
.pas
    margin-left 17px !important
.inputbox
    display flex
    justify-content center
    height 50px
    margin 3% 0
  &input
    width 340px
    height 38px
    border 1px solid gray
    border-radius 4px
    padding 6px
    line-height 2px
.fixbox {
    width: 340px;
    margin-bottom: 12px;
    height: 60px;
    text-align: center;
    display: flex;
    justify-content: center;
}
.check-label
    display: flex;
    align-items: center;
    cursor pointer;
.check-label input{
    width: auto;
}
.submit-button
    background-color #3DA8F5
    border: 1px solid #3DA8F5
    color #fff

.cross{
    margin-left 0 !important
    left -28px !important
    top 15px !important
}
.cross:before{
    margin-left -1.5px !important
    top -3px !important
}
.input-name{
  margin-left: 18px;
}
</style>
<script>
import Eye from '@/components/login/Eye.vue';
import Headi from '@/components/login/Headi.vue';
import Cross from '@/components/login/Cross.vue';

export default {
  components: {
    Eye,
    Headi,
    Cross
  },
  props: {
    account2: {
      type: String,
      required: false,
      default: '',
    }
  },
  data: function() {
    return {
      name: '',
      password: '',
      recheck: '',
      pasType: 'password',
      pas2Type: 'password',
    };
  },
  methods: {
    submitData() {
      if (this.password === this.recheck) {
        console.log('555');
      }
      this.$emit('submit', this.name, this.password);
    },
    changeType() {
      this.pasType = (this.pasType === 'password') ? 'text' : 'password';
    },
    changeType2() {
      this.pas2Type = (this.pas2Type === 'password') ? 'text' : 'password';
    },
    clear() {
      this.name = '';
    }
  },
};
</script>

