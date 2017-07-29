<template>
  <div id="app">
    <h1>Word Traslator</h1>
    <h5>Powered By Vue.js</h5>
    <TranslateForm v-on:formSubmit="translateText"></TranslateForm>
  </div>
</template>

<script>

  import TranslateForm from './components/TranslateForm';

  export default {
    name: 'app',
    components: {
      TranslateForm
    },
    methods: {
      translateText: function(text) {
        this.$http.get('https://translate.yandex.net/api/v1.5/tr.json/translate?key=trnsl.1.1.20170729T111852Z.09e87fb8298020b5.ac85cecbb70daac2e641eaffae5f9640aa34c7eb&lang=ru&text='+text)
          .then((response) => {
            console.log(response.data.text[0]);
          });
      }
    }
  }
</script>

<style>
#app {
 
}
</style>
