<template>
  <div class="hello">
    <h1>{{ msg }}</h1>

    <hr>

    <input type="number" v-model.number.lazy="operand1" ref="input1" />
    <input type="number"  v-model.number.lazy="operand2" ref="input2" />
    <p v-if="result == Infinity">На ноль делить нельзя</p>
    <p v-else>= {{ result }}</p>
    <br>
    <button class ="btn__calc" @click="sum()">+</button>
    <button class ="btn__calc" @click="substract()">-</button>
    <button class ="btn__calc" @click="multiply()">*</button>
    <button class ="btn__calc" @click="degree()">**</button>
    <button class ="btn__calc" @click="divide()">/</button>
    <button class ="btn__calc" @click="remainder()">%</button>
    <button class ="btn__calc" @click="removebutton()">R</button>

    <hr>

    <div class="test">
          <input type="checkbox" id="checkbox" v-model="checked" />Отобразить клавиатуру
          <div v-if="checked == true">
            <div class="btn__wrp">
          <button class="btn" @click="input(num)" v-for="num in numbers" :key="num">{{ num }}</button>
          </div>
        </div>
    </div>
    
    <input @click="foc1()" type="radio" name="test" value="operand1" v-model="picked" />Операнд 1
    <input @click="foc2()" type="radio" name="test" value="operand2" v-model="picked" />Операнд 2
  </div>
</template>



<script>
export default {
  name: 'HelloWorld',
  props: {
    msg: String
  },

  data() {
    return {
      result: '',
      operand1: '',
      operand2: '',
      checked: true,
      numbers: [1, 2, 3, 4, 5, 6, 7, 8, 9, 0],
      operands: ["+", "-", "/", "*","**", "%","<--"],
      picked:[],
    };
  },

  methods: {
    input(test) {
      if(this.picked === "operand1"){
        this.operand1 += parseInt(test)
      }else{
        this.operand2 += parseInt(test)
      }
    },

    removebutton() {
      if(this.operand1.length>1) {
        this.operand1 = this.operand1.slice(0,this.operand1.length-1)
      }else{
        this.operand1=''
      }

      if(this.operand2.length>1) {
        this.operand2 = this.operand2.slice(0,this.operand2.length-1)
      }else{
        this.operand2=''
      }
    },

    calculate(operation) {
      this.error = "";
      switch (operation) {
        case "+":
          this.sum();
          break;
        case "-":
          this.substract();
          break;
        case "*":
          this.multiply();
          break;
        case "**":
          this.degree();
          break;
        case "/":
          this.divide();
          break;
        case "%":
          this.remainder();
          break;
        case "<--":
          this.removebutton();
          break;
      }
    },
    
    foc1() {
        this.$refs.input1.focus();
    },

    foc2() {
        this.$refs.input2.focus();
    },

    sum(){
      this.result = Number(this.operand1) + Number(this.operand2)
    },

    substract() {
      this.result = this.operand1-this.operand2
    },

    divide() {
      this.result = this.operand1 / this.operand2
    },

    multiply() {
      this.result = this.operand1 * this.operand2
    },

    degree() {
      this.result = this.operand1 ** this.operand2
    },

    remainder(){
      this.result = this.operand1 % this.operand2
  },
  },
};

</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}


.btn__wrp {
  display: flex;
  justify-content: center;
  flex-wrap: wrap;
  width: 100px;
  margin: 0 auto;
}
.btn {
  width: 50px;
  height: 50px;
}
.btn__calc {
  width: 30px;
  height: 30px;
  margin: 3px;
}

</style>
