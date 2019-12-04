<template>
  <div id="app">
    <h2>{{msg}}</h2>
  <input type="text" v-model="inputVal" @keydown="add($event)"> <button @click="add(13)">添加数据</button>
  <br>
  <h2>代办项</h2>
  <ul>
    <li v-for="(item,key) in list" v-if="!item.checked">
      <input type="checkbox" v-model="item.checked" @change="saveList()">---{{item.title}}----<button @click="remove(key)">删除数据</button>
    </li>
  </ul>
  <h2>完成项</h2>
  <ul>
    <li v-for="item in list" v-if="item.checked">
      <input type="checkbox" v-model="item.checked" @change="saveList()">---{{item.title}}----<button @click="remove(key)">删除数据</button>
    </li>
  </ul>
  </div>
</template>
<script>
  import storage from './model/storage.js';
  console.log(storage);
export default {
  name: 'app',
  data () {
    return {
      msg: 'vue学习开始',
      inputVal:'',
      list:[]
    }
  },
  methods:{
    add(key){
      console.log(key);
      if (key==13 || key.keyCode==13){
        if(this.inputVal != ''){
          this.list.push({
            'title' : this.inputVal,
            'checked' : false
          });
          storage.set('list',this.list);
          this.inputVal = '';
        }
      }
    },
    remove(key){
        this.list.splice(key,1);
        storage.set('list',this.list);
    },
    saveList(){
      storage.set('list',this.list);
    },
  },
  mounted(){
    var list = storage.get('list');
    if(list){
      this.list = list;
    }
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: left;
  color: #2c3e50;
  margin-top: 60px;
  margin-left: 5%;
}
ul{
  text-align: left;
  /* margin-left: 40%; */
}
ul li{
  margin: 5px 0;
  list-style: none;
}
</style>
