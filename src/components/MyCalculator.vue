<template>
<div class="calculator">
  <div class="k1">{{ result || '0'}}</div>
  <div class="btn k2" @click="clear">C</div>
  <div class="btn k3 " @click="sign">+/-</div>
  <div class="btn k5" @click="percent">%</div>
  <div class="btn k6 sdrow" @click="divide">÷</div>
  <div class="btn k7" @click="append('7')">7</div>
  <div class="btn k8" @click="append('8')">8</div>
  <div class="btn k9" @click="append('9')">9</div>
  <div class="btn k10 sdrow" @click="multiply">X</div>
  <div class="btn k11" @click="append('4')">4</div>
  <div class="btn k12" @click="append('5')">5</div>
  <div class="btn k13" @click="append('6')">6</div>
  <div class="btn k14 sdrow" @click="subtract">-</div>
  <div class="btn k15" @click="append('1')">1</div>
  <div class="btn k16" @click="append('2')">2</div>
  <div class="btn k17" @click="append('3')">3</div>
  <div class="btn k18 sdrow" @click="addition">+</div>
  <div class="btn zero" @click="append('0')">0</div>
  <div class="btn k20" @click="decimal">.</div>
  <div class="btn k21 sdrow" @click="equal">=</div>
  </div>
</template>

<script>
export default {
  name: 'MyCalculator',
  data(){
    return{
      result:'',
      prev:null,
      operator:null,
      operatorClicked:false,
    }
  },
  methods:{
    clear(){
      this.result='';
    },
    percent(){
      this.result=`${parseFloat(this.result)/100}`;
    },
    append(a){
      if(this.operatorClicked){
        this.result='';
        this.operatorClicked=false;
      }
      this.result+=a;
    },
    decimal(){
      if(this.result.indexOf('.')==-1){
        this.result+='.';
      }
    },
      sign(){
        if(this.result.indexOf('-')==-1){
          this.prev=this.result;
          this.result= '-'+this.result;
        }
        else{
          this.result=this.prev;
        }
      },
      addition(){
        this.operator = (a,b) => a+b;
        this.prev=this.result;
        this.operatorClicked=true;
      },
      subtract(){
        this.operator = (a,b) => a-b;
        this.prev=this.result;
      this.operatorClicked=true;
      },
      multiply(){
        this.operator = (a,b) => a*b;
        this.prev=this.result;
        this.operatorClicked=true;      
      },
      divide(){
        this.operator = (a,b) => a/b;
        this.prev=this.result;
        this.operatorClicked=true;      
      },
      equal(){
        this.result=`${this.operator(parseFloat(this.prev),parseFloat(this.result))}`;
      }

    }
  }

</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.calculator{
  width: 500px;
  height: 800px;
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  font-size:45px;
  text-align: center;
  display:grid;
  grid-template-columns: repeat(4,1fr);
  grid-auto-rows: minmax(50px,auto);
}
.k1{
  padding-top:10%;
  grid-column:1/5;
  background-color:black;
  color:white;
}
.zero{
  grid-column: 1/3;
}
.btn{
  background-color: bisque;
  border:1px solid #999;
}
.sdrow{
  background-color: aquamarine;
}
</style>
