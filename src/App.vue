<template>
  <div id="app"  class="text-center">
    <h1 class="text-white header">Word Translator</h1>
    <h5>Powered By Vue.js</h5>
    <TranslateForm v-on:formSubmit="translateText"></TranslateForm>
    <TranslateOutput v-text="translatedText"></TranslateOutput>
  </div>
</template>

<script>

  import TranslateForm from './components/TranslateForm';
  import TranslateOutput from './components/TranslateOutput';

  export default {
    name: 'app',
    components: {
      TranslateForm,
      TranslateOutput
    },
    data: function () 
    {
      return {
        translatedText : ''
      }
    },
    methods: {
      translateText: function(text, language) {
        this.$http.get('https://translate.yandex.net/api/v1.5/tr.json/translate?key=trnsl.1.1.20170729T111852Z.09e87fb8298020b5.ac85cecbb70daac2e641eaffae5f9640aa34c7eb&lang='+language+'&text='+text)
          .then((response) => {
            this.translatedText = response.data.text[0];
          });
      }
    }
  }
</script>

<style>
@import url('https://fonts.googleapis.com/css?family=Amarante|Philosopher&subset=cyrillic');

body, html {
  background: #0288d1;
  font-family: 'Philosopher', sans-serif;
}

#app {
}

#app .header {
  font-size: 55px!important;
  font-family: 'Amarante', cursive;
  color: white;
  text-shadow: 0 1px 3px #000;

}

#app h5 {
  font-size: 25px;
  color: white;
  text-shadow: 0 1px 3px #000;
}
</style>
