<template>
  <div id="app" class="app">
    <h1>Simple Translator</h1>
  	<h2>by Vue.js</h2>
  	<translate-form v-on:submitForm="translateText"></translate-form>
    <translate-output v-text="translatedText"></translate-output>
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
  data() {
    return {
      translatedText: ''
    };
  },
  methods: {
		translateText(text, language) {
			this.$http.get(`https://translate.yandex.net/api/v1.5/tr.json/translate?key=trnsl.1.1.20170729T190953Z.e7f5acb4285a991f.4e1a5dd3bd0f86f20e28396459af831d489217c1&lang=${language}&text=${text}`)
      .then((response) => {
        this.translatedText = response.body.text[0];
      });
		}
	}
}
</script>

<style>
@import url('https://fonts.googleapis.com/css?family=Nunito:400,400i,600,700');

html,
body {
  height: 100%;
}

body {
  display: table;
  margin: 0;
  width: 100%;
	font-family: 'Nunito', sans-serif;
	background: #4568dc; /* fallback for old browsers */
	background: -webkit-linear-gradient(to left, #B06ab3, #4568dc);
	background: linear-gradient(to left, #B06ab3, #4568dc);
}

.app {
  display: table-cell;
  vertical-align: middle;
  padding: 20px 10px;
  font-family: 'Nunito', Helvetica, Arial, sans-serif;
  text-align: center;
  color: #f7f7f7;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}

h1 {
  margin: 10px 0;
	text-transform: uppercase;
}

h2 {
	margin: 10px 0 50px;
}
</style>
