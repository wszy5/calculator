<template>
  <div>
    <div id="result">
      <button id="clb" class="sbtn" @click="clear()">CLEAR</button>
      <div id="math-res">{{this.result}}
</div>
      </div>
    <div id="operators">
      <button v-for="i in operations" :key="i" class="sbtn" @click="clickHandler(i)">{{i}}</button>
    </div>
    <div id="buttons">
        <button v-for="i in Array.from(Array(10).keys())" :key="i" class="sbtn" @click="passValue(i)">{{i}}</button>
        <button class="sbtn" @click="passValue('.')">{{'.'}}</button>
      <button class="sbtn" @click="calculate()">=</button>
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
      z:"",
    }
  },
  methods:{
    passValue(i){
      if(this.result.length<=12){
            if(this.operatorClicked){
              this.temp2 += i.toString();
              this.result += this.temp2
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
      this.temp2 = "";
      this.temp1 = this.result;
      this.operatorClicked = true;
      this.result += z;
      this.z = z;
    },
  calculate()
  {
    if(this.temp1!="" && this.temp2!=""){
      switch (this.z) {
        case '+':
            this.result = (Number.parseFloat(this.temp1)+Number.parseFloat(this.temp2)).toString();
          break;
        case '-':
            this.result = (Number.parseFloat(this.temp1)-Number.parseFloat(this.temp2)).toString();
            break;
        case '*':
            this.result = (Number.parseFloat(this.temp1)*Number.parseFloat(this.temp2)).toString();
        break;
        case '/':
            this.result = (Number.parseFloat(this.temp1)/Number.parseFloat(this.temp2)).toString();
        break;
      
      }
      }
  }
  }
}
</script>

<style>
body{
  margin-top: 100px;
  height: 100%;
  background-image: url('https://cdn.pixabay.com/photo/2017/07/27/02/23/space-2543838_1280.jpg');
  background-repeat: no-repeat;
  background-size: auto;
  display: flex;
  justify-content: center;
}
#app{
  display: flex;
  flex-direction: column;
  
}
#result{
  width: 300px;
  height: 100px;
  background-color: black;
  opacity: 0.67;
  padding: 10px;
  display: flex;
  flex-direction: column;
  justify-content: right;
  align-items: center;
  border: 1px solid black;
  font-size: 32px;
  color: white;
}

#buttons{
  width: 300px;
  display: flex;
  flex-direction: row;
  flex-wrap: wrap;
  justify-content: center;
  align-items: center;
  margin-left: auto;
  margin-right: auto;
  opacity: 0.67;
}
.sbtn{
  display: flex;
  justify-content: center;
  align-items: center;
  width: 65px;
  height: 65px;
  margin: 5px;
    font-size: 3.2em;

}

#operators{
  width: 300px;
  display: flex;
  flex-direction: row;
  flex-wrap: wrap;
  justify-content: center;
  align-items: center;
  margin-left: auto;
  margin-right: auto;
  opacity: 0.67;
}
#operators button{
  background-color: green;
  color: white;
  border: none;
  font-size: 3.2em;
}

.operator{
  background-color: brown;
  color: aliceblue;
  font-weight: bold;
  width: 25px;
  height: 25px;
}
#clb{
  width: 40px;
  height: 20px;
  font-size: 10px;
  align-self: flex-start;
  background-color: red;
  border: none;
  color: aliceblue;
  opacity: 0.5;
  justify-self: flex-end;
  margin-right: 230px;
  }
</style>
