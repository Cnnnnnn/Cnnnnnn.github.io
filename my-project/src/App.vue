<template>
  <div id="app">
    <h1>Cn在线翻译</h1>
    <h5 class="text-muted">简单 / 易用 / 便捷</h5>
    <h5 class="text-muted">设计者：梁世恩</h5>
    <translateForm v-on:formSubmit="translateText"></translateForm>
    <translateOutput v-text="translatedText"></translateOutput>
  </div>
</template>

<script>

import TranslateForm from './components/TranslateForm'
import TranslateOutput from './components/TranslateOutput'

export default {
  name: 'App',
  data:function(){
    return{
      translatedText:""
    }
  },
  components: {
    TranslateForm,TranslateOutput
  },
  methods:{
    translateText:function(text,language){
      // alert(text);
      this.$http.get('https://translate.yandex.net/api/v1.5/tr.json/translate?key=trnsl.1.1.20180313T033403Z.1c473c66c760ce42.ee11b9adc875668e28b45f88f7c0546a55d87a08&lang='+language+'&text='+text).then((response)=>{
          // console.log(response.body.text[0]);
          this.translatedText = response.body.text[0];
      })
    }
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
