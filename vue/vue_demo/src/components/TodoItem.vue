<template>
  <li :style="{background:bgColor}" @mouseenter="handleEnter(true)" @mouseleave="handleEnter(false)">
    <label>
      <input type="checkbox" v-model="todo.complete"/>
      <span>{{todo.title}}</span>
    </label>
    <button class="btn btn-danger" v-show="isShow" @click="deleteItem">删除</button>
  </li>
</template>


<script>
  export default{
    props: {
      todo: Object,
      index: Number,
      deleteTodo: Function
    },
    data(){
      return {
        bgColor: 'white',
        isShow: false
      }
    },
    methods: {
      handleEnter(isEnter){
        if (isEnter) {
          this.isShow = true;
          this.bgColor = 'gray';
        } else {
          this.isShow = false;
          this.bgColor = 'white';
        }
      },
      deleteItem(){
        const {todo, index, deleteTodo} = this;
        if (window.confirm('确认删除' + todo.title + "吗？")) {
          deleteTodo(index)
        }
      }
    }
  }
</script>


<style>
  .todo-main {
    margin-left: 0px;
    border: 1px solid #ddd;
    border-radius: 2px;
    padding: 0px;
  }

  .todo-empty {
    height: 40px;
    line-height: 40px;
    border: 1px solid #ddd;
    border-radius: 2px;
    padding-left: 5px;
    margin-top: 10px;
  }

  /*item*/
  li {
    list-style: none;
    height: 36px;
    line-height: 36px;
    padding: 0 5px;
    border-bottom: 1px solid #ddd;
  }

  li label {
    float: left;
    cursor: pointer;
  }

  li label li input {
    vertical-align: middle;
    margin-right: 6px;
    position: relative;
    top: -1px;
  }

  li button {
    float: right;
    display: none;
    margin-top: 3px;
  }

  li:before {
    content: initial;
  }

  li:last-child {
    border-bottom: none;
  }
</style>
