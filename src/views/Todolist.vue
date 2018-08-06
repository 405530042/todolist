<template>
  <div class="header-content">
    <head-icon></head-icon>
    <div class="main">
      <todo></todo>
    </div>
  </div>
</template>

<style lang="stylus" scoped>
* {
    color: #383838;
    margin: 0;
    padding: 0;
    font-family: '微軟正黑體';
}

.main {
    position: fixed;
    top: 108px;
    right: 0;
    bottom: 0;
    left: 0;
    padding: 0;
    overflow: hidden;
    transition: all 218ms ease;
}

.header-content{
    width: 100%
}

</style>


<script>
import Todo from '@/components/todolist/Todo.vue';
import HeadIcon from '@/components/todolist/HeadIcon.vue';

export default {
  components: {
    Todo,
    HeadIcon
  }
};
</script>

