<template>
  <div id="app">
    <h1>在线翻译</h1>
    <h5 class="text-muted">简单 / 易用 / 便捷</h5>
    <translateForm v-on:submitForm="translating"></translateForm>
    <translateOutput v-bind:translatedText="translatedText"></translateOutput>
  </div>
</template>

<script>
import TranslateForm from './components/translateForm'
import TranslateOutput from './components/translateOutput'

export default {
  name: 'App',
  data: function () {
    return {
      translatedText: ""
    }
  },
  methods: {
    translating: function (text, lang) {
      this.$http.get(`https://translate.yandex.net/api/v1.5/tr.json/translate?key=trnsl.1.1.20180928T151247Z.2e2e8d4cbaf2e98c.0cc1a3b81d2baa944ef3bd2c54febce2400f3f08&lang=${lang}&text=${text}`).then((res)=>{
               this.translatedText = res.body.text[0];
             })
    }
  },
  components: {
    TranslateForm,
    TranslateOutput
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
