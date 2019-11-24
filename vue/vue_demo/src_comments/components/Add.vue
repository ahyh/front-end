<template>
  <div class="col-md-4">
    <form class="form-horizontal">
      <div class="form-group">
        <label>用户名</label>
        <input type="text" class="form-control" placeholder="用户名" v-model="username">
      </div>
      <div class="form-group">
        <label>评论内容</label>
        <textarea class="form-control" rows="6" placeholder="评论内容" v-model="content"></textarea>
      </div>
      <div class="form-group">
        <div class="col-sm-offset-2 col-sm-10">
          <button type="button" class="btn btn-default pull-right" @click="add">提交</button>
        </div>
      </div>
    </form>
  </div>
</template>


<script>
  export default{
    props: {  //指定属性名、属性值类型、必要性
      addComment: {
        type: Function,
        required: true
      }
    },
    data(){
      return {
        username: '',
        content: ''
      }
    },
    methods: {
      add(){
        //1.收集输入的数据封装成一个comment对象，添加到comments中
        const username = this.username.trim();
        const content = this.content.trim();
        const comment = {'name': username, 'content': content};
        this.addComment(comment);
        this.username = '';
        this.content = '';
      }
    }
  }
</script>


<style>

</style>
