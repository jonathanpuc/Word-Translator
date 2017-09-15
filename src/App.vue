<template>
  <div id="app" class="text-center">
    <h1>Word Translator</h1>
    <TranslateForm v-on:formSubmit="translateText"></TranslateForm>
    <TranslateOutput v-text="translatedText"></TranslateOutput>
  </div>
</template>

<script>
import TranslateForm from './components/TranslateForm'
import TranslateOutput from './components/TranslateOutput'
export default {
  name: 'app',
  components: {
    TranslateForm,
    TranslateOutput
  },
  data () {
    return {
      translatedText:''
    }
  },
  methods: {
    translateText (text, language){
      this.$http.get('https://translate.yandex.net/api/v1.5/tr.json/translate?key=trnsl.1.1.20170914T095823Z.dc0b13b6f0946d55.6c8c4f5a4934b3b38cc810e9a92ea7a592c16b82&lang='+language+'&text='+text+'&format=plain')
      .then((response) => {
        this.translatedText = response.body.text[0];
      });
    }
  }
}
</script>

<style>
@import url('https://fonts.googleapis.com/css?family=Anton');

body {
  background:rgb(39,33,61);
}

h1 {
  color:white;
  font-family: 'Anton', sans-serif;
}
</style>
