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
        <td class="button grey" @click="addNumber(7)">7</td>
        <td class="button grey" @click="addNumber(8)">8</td>
        <td class="button grey" @click="addNumber(9)">9</td>
        <td class="button orange" @click="setOperator('*')">*</td>
      </tr>
      <tr>
        <td class="button grey" @click="addNumber(4)">4</td>
        <td class="button grey" @click="addNumber(5)">5</td>
        <td class="button grey" @click="addNumber(6)">6</td>
        <td class="button orange" @click="setOperator('-')">-</td>
      </tr>
      <tr>
        <td class="button grey" @click="addNumber(1)">1</td>
        <td class="button grey" @click="addNumber(2)">2</td>
        <td class="button grey" @click="addNumber(3)">3</td>
        <td class="button orange" @click="setOperator('+')">+</td>
      </tr>
      <tr>
        <td class="button-col2 grey" @click="addNumber(0)" colspan="2">0</td>
        <td class="button grey" @click="addPoint">.</td>
        <td class="button orange" @click="equal">=</td>
      </tr>
    </table>
  </div>
</template>

