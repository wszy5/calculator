<template>
  <div id="app">
    <div id="result">{{this.a}}{{this.b}}</div>
    <div id="buttons">
        <button v-for="i in Array.from(Array(10).keys())" :key="i" class="sbtn" @click="passValue(i)">{{i}}</button>
        <button class="sbtn" @click="clear()">CLEAR</button>
        <button class="sbtn">=</button>
    </div>
  </div>
</template>

<script>

export default {
  name: 'App',
  data(){
    return{
      a:null,
      b:null,
      result:null
    }
  },
  methods:{
    passValue(i){
      if(this.a==null){
        this.a = i;
      }
      else{
        this.b = i;
      }
    },
    show(){
      alert(this.a);
      alert(this.b);
    },
    clear(){
      this.a = null,
      this.b = null,
      this.result = null
    }
  }
}
</script>

<style>

#result{
  width: 200px;
  height: 100px;
  background-color: antiquewhite;
  padding: 10px;
  display: flex;
  justify-content: center;
  align-items: center;
  border: 1px solid black;
  font-size: 32px;
}

#buttons{
  width: 200px;
  display: flex;
  flex-direction: row;
  flex-wrap: wrap;
  justify-content: center;
  align-items: center;
  
}
.sbtn{
  display: flex;
  justify-content: center;
  align-items: center;
  width: 55px;
  height: 55px;
  margin: 5px;
}
</style>
