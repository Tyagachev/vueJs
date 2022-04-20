<template>
  <div class="hello">
    <h1>{{ msg }}</h1>

    <hr>

    <input v-model.number="operand1" ref="input1" />
    <input v-model.number="operand2" ref="input2" />
    <p v-if="result == Infinity">На ноль делить нельзя</p>
    <p v-else>= {{ result }}</p>
    <br>
    <button @click="sum()">+</button>
    <button @click="substract()">-</button>
    <button @click="multiply()">*</button>
    <button @click="divide()">/</button>

    <hr>

    <div class="test">
          <input type="checkbox" id="checkbox" v-model="checked" />Отобразить клавиатуру
          <div v-if="checked == true">
          <button @click="input(num)" v-for="num in numbers" :key="num">{{ num }}</button>
        </div>
    </div>
    
    <input @click="foc1()" type="radio" name="test" value="operand1" v-model="picked" />Операнд 1
    <input @click="foc2()" type="radio" name="test" value="operand2" v-model="picked" />Операнд 2
    <!--<div v-for="pic in picked" :key="pic">{{pic}}</div>-->

    
  


    <!--<p>
      For a guide and recipes on how to configure / customize this project,<br>
      check out the
      <a href="https://cli.vuejs.org" target="_blank" rel="noopener">vue-cli documentation</a>.
    </p>
    <h3>Installed CLI Plugins</h3>
    <ul>
      <li><a href="https://github.com/vuejs/vue-cli/tree/dev/packages/%40vue/cli-plugin-babel" target="_blank" rel="noopener">babel</a></li>
      <li><a href="https://github.com/vuejs/vue-cli/tree/dev/packages/%40vue/cli-plugin-router" target="_blank" rel="noopener">router</a></li>
      <li><a href="https://github.com/vuejs/vue-cli/tree/dev/packages/%40vue/cli-plugin-vuex" target="_blank" rel="noopener">vuex</a></li>
      <li><a href="https://github.com/vuejs/vue-cli/tree/dev/packages/%40vue/cli-plugin-eslint" target="_blank" rel="noopener">eslint</a></li>
      <li><a href="https://github.com/vuejs/vue-cli/tree/dev/packages/%40vue/cli-plugin-unit-mocha" target="_blank" rel="noopener">unit-mocha</a></li>
      <li><a href="https://github.com/vuejs/vue-cli/tree/dev/packages/%40vue/cli-plugin-e2e-cypress" target="_blank" rel="noopener">e2e-cypress</a></li>
    </ul>
    <h3>Essential Links</h3>
    <ul>
      <li><a href="https://vuejs.org" target="_blank" rel="noopener">Core Docs</a></li>
      <li><a href="https://forum.vuejs.org" target="_blank" rel="noopener">Forum</a></li>
      <li><a href="https://chat.vuejs.org" target="_blank" rel="noopener">Community Chat</a></li>
      <li><a href="https://twitter.com/vuejs" target="_blank" rel="noopener">Twitter</a></li>
      <li><a href="https://news.vuejs.org" target="_blank" rel="noopener">News</a></li>
    </ul>
    <h3>Ecosystem</h3>
    <ul>
      <li><a href="https://router.vuejs.org" target="_blank" rel="noopener">vue-router</a></li>
      <li><a href="https://vuex.vuejs.org" target="_blank" rel="noopener">vuex</a></li>
      <li><a href="https://github.com/vuejs/vue-devtools#vue-devtools" target="_blank" rel="noopener">vue-devtools</a></li>
      <li><a href="https://vue-loader.vuejs.org" target="_blank" rel="noopener">vue-loader</a></li>
      <li><a href="https://github.com/vuejs/awesome-vue" target="_blank" rel="noopener">awesome-vue</a></li>
    </ul>-->
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
      operand1: 0,
      operand2: 0,
      checked: true,
      numbers: [1, 2, 4, 5, 6, 7, 8, 9, 0],
      operands: ["+", "-", "/", "*"],
      picked:[],
    };
  },

  methods: {
    input(test) {
      if(this.picked==this.operand1){
        this.operand1+=test
      }
      if(this.picked==this.operand2){
        this.operand2+=test
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
        case "/":
          this.divide();
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
      this.result = this.operand1 + this.operand2
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
</style>
