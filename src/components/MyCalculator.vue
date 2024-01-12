<template>
<div class="calculator">
  <div class="k1">{{ result || '0'}}</div>
  <div class="btn k2" @click="clear">C</div>
  <div class="btn k3 ">+/-</div>
  <div class="btn k5" @click="percent">%</div>
  <div class="btn k6 sdrow">÷</div>
  <div class="btn k7" @click="append('7')">7</div>
  <div class="btn k8">8</div>
  <div class="btn k9">9</div>
  <div class="btn k10 sdrow">X</div>
  <div class="btn k11">4</div>
  <div class="btn k12">5</div>
  <div class="btn k13">6</div>
  <div class="btn k14 sdrow">-</div>
  <div class="btn k15">1</div>
  <div class="btn k16">2</div>
  <div class="btn k17">3</div>
  <div class="btn k18 sdrow">+</div>
  <div class="btn zero">0</div>
  <div class="btn k20">.</div>
  <div class="btn k21 sdrow">=</div>
  </div>
</template>

<script>
export default {
  name: 'MyCalculator',
  data(){
    return{
      result:'2987',
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
      this.result+=a;
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
