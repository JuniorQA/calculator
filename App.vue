<template>
  <div id="app">
    <div class="main-container">
    <div class="input-container">
        <input type="text" class="calc-input" v-model="result">
    </div>
    <div class="buttons-section-container">
      <calcButton  v-for = '(item, index) in buttonValue'
    v-bind:key = 'item'
    v-bind:index = 'index'
    v-bind:item = 'item'
    v-bind:buttonValue = "buttonValue"
    v-bind:result = "result"
    v-on:pushToInput="pushToInput"
    />
  </div>
      <resBtn
      v-bind:result="result"
      v-on:calcEvent="calcEvent"
    />
    </div>
  </div>
</template>

<script>
import calcButton from '@/components/button'
import resBtn from '@/components/resBtn'
export default {
  name: 'App',
  data(){
    return{
        buttonValue: [1,2,3,4,5,6,7,8,9,'+',0,'-','*','/','C'],
        result : '',
        nums: [],
        operators: [],
        calcRes : 0,
    }
  },
  methods: {
    pushToInput(item) {
      if (item === 'C') {
        this.result = '';
      }
      else this.result += item;
    },

    selectNums(res) {
      let num = '';
      for (let i = 0; i < res.length; i++) {
        if (!isNaN(Number(res[i]))) {
          num += res[i];
        }
        if (i === res.length - 1 && !isNaN(Number(res[i]))) {
          this.nums.push(Number(num));
        }
        else if (isNaN(Number(res[i]))) {
          this.operators.push(res[i]);
          this.nums.push(Number(num));
          num = '';
        }
      }
    },

    calculate() {
      this.calcRes = this.nums[0];
      for (let i = 0; i < this.nums.length - 1; i++) {
         switch(this.operators[i]) {
           case '+' : 
            this.calcRes += Number(this.nums[i + 1]);
            break;
           case '-' :
            this.calcRes = this.calcRes - Number(this.nums[i + 1]);
            break;
           case '*' :
            this.calcRes = this.calcRes * Number(this.nums[i + 1]);
            break;
           case '/' :
            this.calcRes = this.calcRes / Number(this.nums[i + 1]);
            break;
         }
      }
      this.result = this.calcRes;
    },

    calcEvent(res) {
      this.selectNums(res);
      this.calculate();
      this.nums = [];
      this.operators = [];
    },
  },
  components: {
    calcButton, 
    resBtn
  }
}
</script>

<style src="./app.css"></style>
