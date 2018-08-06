<template>
  <div>
    <headi></headi>
    <form @submit.prevent="delieve">
      <div class="interface login">
        <div class="inputbox bar">
          <input
            :vlaue="account"
            type="text"
            placeholder="信箱/手機號碼"
            required
            @input="account=$event.target.value">
          <eye></eye>
        </div>
        <div class="inputbox">
          <div class="fixbox">
            <input
              class="submit-button"
              type="submit"
              value="立即開始">
          </div>
        </div>
      </div>
    </form>
  </div>
</template>

<style lang="stylus" scoped>
input[type="submit"]
    background-color #03a9f4
    color #fff

input[tpye="checkbox"]
    width 30px !important
    height 30px

select
    border 0
    border-border-radius 4px

a
    text-text-decoration none
    color #03a9f4
    font-size 14px
  &:hover
    color #3da8f5

.header
    justify-content center
    align-items flex-end
    width 100
    height 190px
    display flex

.headimg
    height (100/2)
    display flex
    align-items center
    margin-bottom 22px
  &img
    height 100/3

.phone
    height 50px
    border 1.2px solid gray
    border-border-radius 4px 0 0 4px
    display flex

.check-label {
    display: flex;
    align-items: center;
}

.inputbox {
    display: flex;
    justify-content: center;
    height: 50px;
    margin: 5% 0;
}

.inputbox input {
    width: 340px;
    height: 38px;
    border: 1px solid gray;
    border-radius: 4px;
    padding: 6px;
    line-height: 2px;
}
.bar
    margin-left: 15px;

.fixbox {
    width: 340px;
    margin-bottom: 12px;
    height: 60px;
    text-align: center;
    display: flex;
    justify-content: center;
}

.submit-button
    background-color #3DA8F5
    border: 1px solid #3DA8F5 !important
    cursor pointer
    transition font-size 0.25s
  &:hover
    font-size 1em

</style>

<script>
import Eye from '@/components/login/Eye.vue';
import Headi from '@/components/login/Headi.vue';
export default {
  components: {
    Eye,
    Headi
  },
  data: function() {
    return {
      account: '',
    };
  },
  methods: {
    delieve: function() {
      var i = this.account.indexOf('@');
      // judge if input is email or not
      if (i > -1 && this.account.length > 5) {
        this.$emit('delieve-email', this.account);
      }
      else {
        if ((i === -1 && this.account.length < 11) || this.account.length > 11) {
          alert('手機號碼或郵箱輸入錯誤');
        }
        else if (i > -1 && this.account.length < 5) {
          alert('郵箱輸入有誤');
        }
        else {
          this.$emit('delieve-phone', this.account);
        }
      }
    },
  },
};
</script>

