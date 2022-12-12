<template>
  <div class="calculator">
    <table cellspacing="10">
      <tr>
        <td colspan="4">
          <input type="text" v-model="result" disabled>
        </td>
      </tr>
      <tr>
        <td class="button dark" @click="clear">C</td>
        <td class="button dark" @click="invert">+/-</td>
        <td class="button dark" @click="percent">%</td>
        <td class="button orange" @click="setOperator('/')">/</td>
      </tr>
      <tr>
        <td class="button grey" @click="addNum(7)" >7</td>
        <td class="button grey" @click="addNum(8)">8</td>
        <td class="button grey" @click="addNum(9)">9</td>
        <td class="button orange" @click="setOperator('*')" >*</td>
      </tr>
      <tr>
        <td class="button grey" @click="addNum(4)">4</td>
        <td class="button grey" @click="addNum(5)">5</td>
        <td class="button grey" @click="addNum(6)">6</td>
        <td class="button orange" @click="setOperator('-')" >-</td>
      </tr>
      <tr>
        <td class="button grey" @click="addNum(1)">1</td>
        <td class="button grey" @click="addNum(2)">2</td>
        <td class="button grey" @click="addNum(3)">3</td>
        <td class="button orange" @click="setOperator('+')">+</td>
      </tr>
      <tr>
        <td class="button-col2 grey" colspan="2" @click="addNum(0)">0</td>
        <td class="button grey" @click="addPoint">.</td>
        <td class="button orange" @click="equal">=</td>
      </tr>
    </table>
  </div>
</template>

<script>


export default {
  name: 'HelloWorld',
  data() {
    return {
      result: 0,
      reset: false,
      value: 0,
      operator: undefined
    }
  },
  methods: {
    // вносим цифры и делаем из них простейшую сущность
    addNum(number) {
      if(this.result == 0 || this.reset === true) {
        this.result = ''
        this.reset = false
      }
      this.result += number.toString()
    },

    // в зависимости от используемого оператора через цикл свитч выбираем расчет нужного выражения
    calculate() {
      let value = 0;
      let firstNum = parseFloat(this.value);
      let secondNum = parseFloat(this.result);

      switch(this.operator) {
        case '+':
          value = firstNum + secondNum;
          break;
        case '-':
          value = firstNum - secondNum;
          break;
        case '*':
          value = firstNum * secondNum;
          break;
        case '/':
          value = firstNum / secondNum;
      }
      this.result = value.toString();
     },
    // очищаем все входные данные
    clear() {
      this.result = 0
      this.value = 0
      this. operator = 0
    },

    // меняем знак на противоположный
    invert() {
      this.result *= -1
    },

    // получаем проценты
    percent() {
      this.result /= 100
    },
    // перед выполнением действия оператора заносим данные из резалта в вэлью, если не нажать сумму, можно продложать выполнения ранее выбранного оператора
    setOperator(operator) {
      if (this.value != 0)
        this.calculate()
        this.value = this.result;
        this.operator = operator;
        this.reset = true;
      },
    // получаем результат и обнуляем вэлью, стираем дейсвтие оператора
    equal() {
      this.calculate();
      this.value = 0;
      this.operator = undefined;
      },
    // если в резалте еще нет точки, можем ее добавить
    addPoint() {
      if(!this.result.includes('.'))
        this.result += '.';
    }
  }
}


</script>

