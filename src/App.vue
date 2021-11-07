<template>
  <div id="app">
    <div id="result">{{this.result}}</div>
    <div id="operators">
      <button v-for="i in operations" :key="i" class="operator" @click="clickHandler(i)">{{i}}</button>
    </div>
    <div id="buttons">
        <button v-for="i in Array.from(Array(10).keys())" :key="i" class="sbtn" @click="passValue(i)">{{i}}</button>
      
        <button class="sbtn" @click="clear()">CLEAR</button>
        <button class="sbtn" @click="calculate()">=</button>
        <button>{{this.temp1}}</button>
        <button>{{this.temp2}}</button>
    </div>
  </div>
</template>

<script>

export default {
  name: 'App',
  data(){
    return{
      operations:['+','-','*','/'],
      result:"",
      temp1:"",
      temp2:"",
      operatorClicked:false,
      z:""
    }
  },
  methods:{
    passValue(i){
      if(this.result.length<=12){
            if(this.operatorClicked){
              this.temp2 += i.toString();
            }
            else{
              this.result += i.toString();

            }
      }
    },
    
    clear(){
      this.result = "";
      this.temp1 = "";
      this.temp2 = "";
      this.operatorClicked = false;
      this.z = "";
    },
    clickHandler(z){
      this.temp1 = this.result;
      this.operatorClicked = true;
      this.result = "";
      this.z = z;
    },
  calculate()
  {
    if(this.temp1!="" && this.temp2!=""){
      switch (this.z) {
        case '+':
            this.result = (Number.parseInt(this.temp1)+Number.parseInt(this.temp2)).toString();
          break;
        case '-':
            this.result = (Number.parseInt(this.temp1)-Number.parseInt(this.temp2)).toString();
            break;
        case '*':
            this.result = (Number.parseInt(this.temp1)*Number.parseInt(this.temp2)).toString();
        break;
        case '/':
            this.result = (Number.parseInt(this.temp1)/Number.parseInt(this.temp2)).toString();
        break;
      
      }
      }
  }
  }
}
</script>

<style>
*{
  background-color: aquamarine;
}
#result{
  width: 180px;
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

#operators{
  width: 200px;
  display: flex;
  flex-direction: row;
  justify-content: space-evenly;
  margin-top: 5px;
}

.operator{
  background-color: brown;
  color: aliceblue;
  font-weight: bold;
  width: 25px;
  height: 25px;
}

</style>
