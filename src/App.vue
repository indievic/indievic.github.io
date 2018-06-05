<template>
  <div id="app">
    <div class="container">
      <div class="calc">
        <div class="calc-title">
          <h1 class="title">
            <span v-text="zl"></span>
            <span v-show="parseInt(zl) > 0"> zł</span>
          </h1>
          <h2 class="subtitle">
            = <span v-text="rub"></span>
            <span v-show="parseInt(rub) > 0"> руб</span>
          </h2>
        </div>
        <div class="columns is-mobile">
          <div class="column"><span @click="num(1)" class="button is-link is-outlined">1</span></div>
          <div class="column"><span @click="num(2)" class="button is-link is-outlined">2</span></div>
          <div class="column"><span @click="num(3)" class="button is-link is-outlined">3</span></div>
        </div>
        <div class="columns is-mobile">
          <div class="column"><span @click="num(4)" class="button is-link is-outlined">4</span></div>
          <div class="column"><span @click="num(5)" class="button is-link is-outlined">5</span></div>
          <div class="column"><span @click="num(6)" class="button is-link is-outlined">6</span></div>
        </div>
        <div class="columns is-mobile">
          <div class="column"><span @click="num(7)" class="button is-link is-outlined">7</span></div>
          <div class="column"><span @click="num(8)" class="button is-link is-outlined">8</span></div>
          <div class="column"><span @click="num(9)" class="button is-link is-outlined">9</span></div>
        </div>
        <div class="columns is-mobile">
          <div class="column"><span @click="clear" class="button is-link is-danger">Сброс</span></div>
          <div class="column is-4"><span @click="num(0)" class="button is-link is-outlined">0</span></div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>

export default {
  name: 'app',
  data () {
    return {
      input: '0'
    }
  },
  methods: {
    num(digit) {
      if (this.input.length > 6) return
      if (this.input === '0') {
        this.input = digit.toString();
      } else {
        this.input = `${parseInt(this.input)}` + digit.toString();
      }
    },

    clear() {
      this.input = '0';
    }
  },

  computed: {
    zl() {
      return Number(this.input).toLocaleString();
    },
    rub() {
      return (this.input * 17).toLocaleString();
    },
  }
}
</script>

<style>
  .calc {
    transform: scale(1.3) !important;
  }
  body, html {
    width: 100vw;
    height: 100vh;
    padding: 0 !important;
    margin: 0 !important;
    overflow: hidden !important;
  }
  .container { padding-top: 150px !important; }
  .columns, .calc-title {
    max-width: 200px;
    margin-left: auto !important;
    margin-right: auto !important;
  }
  .calc-title {
    padding: 0 12px 30px !important;
  }
  .button { display: block !important; }
</style>
