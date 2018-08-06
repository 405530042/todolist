<template>
  <ul class="menu">
    <li
      v-for="item in header"
      :key="item.id">
      <h3>{{ item.content }}</h3>
      <div :class="item.id">
        <div
          v-for="(post,index) in item.post"
          :key="post.id"
          class="dolist"
        >
          <label class="task-box">
            <input
              type="checkbox"
              class="checkbox"
              @click="ch(post.text,index,item.id)">
            {{ post.text }}
          </label>
        </div>
      </div>
      <div>
        <div :class="item.visible2">
          <div
            class="create-button"
            @click="task(item.id)">
            <div class="create-icon"></div>
            <div
              class="create-button"
              type="submit">新增任務</div>
          </div>
        </div>
        <div
          :class="item.visible"
          class="test">
          <div
            class="newtask"
          >
            <div class="textareabox">
              <textarea
                v-model="item.textarea"
                @blur="hide"></textarea>
            </div>
            <input
              class="new-button"
              type="button"
              value="創建"
              @click="createTask(item.id)">
          </div>
        </div>
      </div>
    </li>
  </ul>
</template>

<style lang="stylus" scoped>

.undo{
    margin-top:14.5px;
}
.menu {
    list-style-type: none;
    position: relative;
    height: 100%;
    background-color: #fff;
    border: 0 solid #e5e5e5;
    overflow-y: hidden;
    overflow-x: hidden;
    -webkit-overflow-scrolling: touch;
    display: flex;
    padding: 5px 0.3%;
}


.menu li {
    background-color: #eee;
    width: 288px !important;
    margin: 0 0.3% 0 0.47%;
    border: 1px solid #eee;
    border-radius: 3px;

}

.menu h3 {
    color: #383838;
    margin: 4.5% 6%;
    font-size: 15px;
    font-weight: 700;
    letter-spacing: 0.2px;
}

.dolist {
    width: 95%;
    height: 52px;
    background-color: #fff;
    margin: 3% 2.5%;
    font-size: 1.5em;
    letter-spacing: 1px;
    box-shadow: 0px 1px 0px 0px #b6b6b6;
    border-radius: 5px;
    cursor: grab;
    display:flex;
    font-size: 15px;
    color:#383838;

}

.dolist:active {
    transform: translateX();
    cursor: grabbing;
}

.newtask {
    width: 90%;
    z-index: 1;
    background-color: #fff;
    margin: 5% 4%;
    height: 250px;
    border: 2px solid #fff;
    border-radius: 4px;
    transition:opacity 0.5s;
}

.textareabox {
    margin: 1.5%;
    display: flex;
    justify-content: center;
    align-content: center;
    padding: 1px;
    border-bottom: 1px solid #e5e5e5;
    width:95%;
}

.textareabox textarea {
    width: 95%;
    margin-top: 15px;
}

.create-button {
    width: max-content;
    z-index: 100;
    cursor: pointer;
    font-size: 15px;
    align-items: center;
    padding: 0px 8px;
    color: #3db8f3;
    font-weight: 900;
    display: flex;
    margin:0 15px;
    height:24px;
    position:absolute;
}

.create-button:hover {
    color: #0c92f3;
}

.create-icon {
    width: 15px;
    height: 15px;
    border: 1px solid #3db8f3;
    border-radius: 100%;
    background-color: #3db8f3;
}

.create-icon:before {
    margin-left: -5.7px;
    top: 0.3px;
    content: '+';
    height: 10px;
    font-size: 16px;
    font-weight: 900;
    position: absolute;
    color: #fff;
}

input.new-button[type="button"] {
    width: 72px;
    background-color: #3da8f5;
    cursor: pointer;
    color: #fff;
    border: 1px solid #3da8f5;
    border-radius: 3px;
    font-size: 14px;
    float:right;
    margin:2px 25px;
}

input.checkbox{
    width:20px;
    height:20px;
    margin-top:3px;
    margin-left: 12px;
    margin-right: 15px;
}

div.dolist::before{
    content: '';
    width:0px;
    transition: width 0.25s;
    background-color: #b6b6b6;
    border-radius: 4px 0 0 4px;
}
div.dolist:hover::before{
    width:8px;
}

.task-box{
    cursor:pointer;
    display:flex;
    align-items:center;
}

.hidden{
    display:none;
}
.show{
    display:block;
}
</style>

<script>
export default {
  data() {
    return {
      header: [
        { 
          id: 1,
          content: '待處理',
          count: 0,
          visible: 'hidden',
          visible2: 'show',
          textarea: '',
          post: [{ id: -2,
            text: 'tt'
          },
          { id: -1,
            text: '123123'
          }]
        },
        { id: 2,
          count: 0,
          textarea: '',
          visible: 'hidden',
          visible2: 'show',
          content: '進行中',
          post: [{ id: 1,
            text: 'tt2' }]},

        { id: 3,
          count: 0,
          textarea: '',
          visible: 'hidden',
          visible2: 'show',
          content: '已完成',
          post: [{ id: 1,
            text: 'tt3' }]},

      ],
    };
  },
  methods: {
    ch(message, index, id) {
      if (id === 3) {
        this.header[id - 1].post.splice(index, 1);
      }
      else {
        this.header[2].post.push({
          id: this.header[2].count ++,
          text: message
        });
        this.header[id - 1].post.splice(index, 1);
      }
    },
    createTask(id) {
      this.header[id - 1].post.push({
        id: this.header[id - 1].count ++,
        text: this.header[id - 1].textarea,
      });
      this.header[id - 1].textarea = '';
      this.header[id - 1].visible2 = 'show';
      this.$nextTick(() => {
        this.header[id - 1].visible = 'hidden';
      });
    },
    task(id) {
      console.log('tt');
      this.header[id - 1].visible = 'show';
      this.$nextTick(() => {
        this.header[id - 1].visible2 = 'hidden';
      });
    },
    hide() {
      console.log('5556');
    },
  }
};
</script>
