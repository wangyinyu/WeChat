<template>
  <div id="app">
    <h2>{{msg}}</h2>
  <input type="text" v-model="inputVal"> <button @click="add()">添加数据</button>
  <br>
  <h2>代办项</h2>
  <ul>
    <li v-for="(item,key) in list" v-if="!item.checked">
      <input type="checkbox" v-model="item.checked">---{{item.title}}----<button @click="remove(key)">删除数据</button>
    </li>
  </ul>
  <h2>完成项</h2>
  <ul>
    <li v-for="item in list" v-if="item.checked">
      <input type="checkbox" v-model="item.checked">---{{item.title}}----<button @click="remove(key)">删除数据</button>
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
      inputVal:'',
      list:[]
    }
  },
  methods:{
    add(){
		if(this.inputVal == ''){
			alert('没有输入数据哦~');
		}else{
			this.list.push({
        'title' : this.inputVal,
        'checked' : false
      });
      this.inputVal = '';
		}
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
