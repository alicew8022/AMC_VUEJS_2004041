<template>
  <div id="app">
    <div class="container">
      <h1>TODO!</h1>
      <p>Simple & Studid Todo APP</p>
      <div class="inputs">
        <input type="text" v-model="msg" class="input_add" placeholder="做點重要的事吧！">
        <button @click="addItem" class="btn_add">ADD</button>
      </div>
      <div class="board">
        <ul class="insert_here">
          <li v-for="(item, index) in items" :key="index" :class="{ 'active': item.completed }">
            <input type="checkbox" v-model="item.completed"> {{ item.text }}
            <button @click="deleteItem(index)" class="btn_delete">－</button>
          </li>
        </ul>
      </div>
    </div>
  </div>
</template>
<script>
export default {
  data() {
    return {
      msg: '', 
      items: []
    };
  },
  methods: {
    addItem() {
      if (this.msg.trim() !== '') {
        this.items.push({ text: this.msg, completed: false });
        this.msg = '';
      }
    },
    deleteItem(index) {
      this.items.splice(index, 1);
    }
  }
};
</script>
<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
body{
  background: #f9f9f9;
}
.container{
  max-width: 1140px;
  margin: 0 auto;
}
.inputs{
  width: 100%;
  box-sizing: border-box;
  padding: 2rem;
  background-color: #fff;
  display: inline-block;
  border-radius: 10px;
  border: 1px solid #ddd;
}
.inputs .input_add{
  width: calc(100% - 100px);
  display: inline-block;
  height: 60px;
  line-height: 60px;
  border: 1px solid #7A99C9;
  outline: none;
  font-size: 1.2rem;
  vertical-align: middle;
  box-sizing: border-box;
  padding: .5rem 1rem;
  border-radius: 5px 0 0 5px;
}
.inputs .btn_add{
  width: 100px;
  display: inline-block;
  border: 0;
  background-color: #7A99C9;
  color: #fff;
  height: 60px;
  line-height: 60px;
  vertical-align: middle;
  border-radius: 0 5px 5px 0;
  font-size: 1.2rem;
}
.insert_here{
  width: 100%;
  box-sizing: border-box;
  display: inline-block;
  padding: 2rem;
  background-color: #fff;
  display: inline-block;
  border-radius: 10px;
  border: 1px solid #ddd;
}
.insert_here li{
  width: 100%;
  display: inline-block;
  border: 1px solid #ccc;
  list-style: none;
  height: 60px;
  line-height: 60px;
  font-size: 1.2rem;
  color: #333;
  margin-bottom: 1rem;
  border-radius: 5px;
  text-align: left;
}
.insert_here li input[type="checkbox"]{
  width: 25px;
  height: 25px;
  vertical-align: text-bottom;
  margin-left: 20px;
  margin-bottom: -1px;
}
.btn_delete{
  width: 35px;
  height: 35px;
  background-color: #7A99C9;
  color: #fff;
  border-radius: 50%;
  float: right;
  border: 0;
  font-size: 1.5rem;
  vertical-align: middle;
  margin: 13px 20px 0 0; 
}
.active{
  text-decoration: line-through;
}
</style>
