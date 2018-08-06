<template>
  <div class="phone-area">
    <headi></headi>
    <form @submit.prevent="submitData">
      <div class="sign">
        <div class="inputbox phone">
          <div class="phone-content">
            <select v-model="value">
              <option
                v-for="option in select"
                :value="option.value"
                :key="option.id">{{ option.text }}</option>
            </select>
            <input
              :value="value"
              type="text"
              class="phone-number">
          </div>
          <input
            v-model="account2"
            :placeholder="account2"
            class="sign-account bdr"
            readonly
            disable>
        </div>
        <div class="inputbox pas">
          <input
            :value="name"
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
    margin 2% 0
  &input
    width 340px
    height 38px
    border 1px solid gray
    border-radius 4px
    padding 6px
    line-height 2px
.phone-content
    display flex
    width (100/2)%
.phone
    display: inline-flex;
    width 354px;
    margin 0
    border-radius 4px
    border 1.2px solid gray
.bdr
    border 0 !important
    border-radius 0!important
.phone-number
    width:50% !important;
    border-right:0.5px solid;
    border-radius: 0px !important;
    border-top:0px !important;
    border-bottom: 0px !important;
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
    cursor pointer
.check-label input{
    width: auto;
}
.cross{
    margin-left 0 !important
    left -28px !important
    top 15px !important
}
.cross:before{
    margin-left -1.5px !important
    top -3px !important
}
.submit-button
    background-color #3DA8F5
    border: 1px solid #3DA8F5
    color #fff
    cursor pointer
</style>
<script>
import Eye from '@/components/login/Eye.vue';
import Cross from '@/components/login/Cross.vue';
import Headi from '@/components/login/Headi.vue';

export default {
  components: {
    Eye,
    Cross,
    Headi
  },
  props: {
    account2: {
      type: String,
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
      value: '',
      select: [{
        text: '中國',
        value: '+86'
      },
      {
        text: '香港',
        value: '+85'
      },
      {
        text: '台灣',
        value: '+886'
      },
      {
        text: '美國',
        value: '+1'
      },
      {
        text: '其他',
        value: ''
      },
      ],
    };
  },
  methods: {
    submitData() {
      if (this.password === this.recheck) {
        this.$emit('submit', this.name, this.password);
      }
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

