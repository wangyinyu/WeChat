<template>
  <div id="app">
  <input type="text" v-model="msg"> <button @click="add()">添加数据</button>
  <h2>{{msg}}</h2>
  <br>
  <ul>
    <li v-for="(item,key) in list">
      {{item}}<button @click="remove(key)">删除数据</button>
    </li>
  </ul>
  </div>
</template>

<script>
export default {
  name: 'app',
  data () {
    return {
      msg: 'vue学习开始',
      list:[]
    }
  },
  methods:{
    add(){
        this.list.push(this.msg)
    },
    remove(key){
        this.list.splice(key,1);
    }
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
