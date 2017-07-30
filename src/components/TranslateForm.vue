<template>
  <div id="translate-form" class="translate-form">
		<form v-on:submit="submitForm">
			<input type="text" v-model="textToTranslate" placeholder="Enter a word...">
      <div class="select-wrap">
        <select id="language-select"
                class="language-select turnintodropdown"
                name="language-select"
                v-model="language">
          <option value="ru" disabled>Language</option>
          <option value="ru">Russian</option>
          <option value="it">Italian</option>
          <option value="fr">French</option>
          <option value="da">Danish</option>
          <option value="zh">Chinese</option>
        </select>
      </div>
			<button type="submit">Translate</button>
		</form>
	</div>
</template>

<script>
import customSelect from './../assets/select/select.js'

export default {
  name: 'translate-form',
  data() {
    return {
      textToTranslate: '',
      language: ''
    }
  },
  created() {
    this.language = 'ru'
  },
  methods: {
		submitForm(e) {
      if (this.textToTranslate) {
        this.language = document.querySelector('#language-select').value;
        this.$emit('submitForm', this.textToTranslate, this.language);
      }
      e.preventDefault();
		}
	}
}
</script>

<style>
a {
  text-decoration: none;
}

input[type=text],
button[type=submit],
.trigger,
.activetrigger {
	padding: 10px 15px;
	border: 0;
	border-radius: 4px;
  font-size: 16px;
	user-select: none;
	transition: .2s background-color ease-in .1s, .2s box-shadow ease-in .1s;
}

input[type=text],
button[type=submit],
.select-wrap {
  margin-bottom: 20px;
}

input[type=text],
.trigger,
.activetrigger {
	margin-right: 5px;
	font-family: 'Nunito', sans-serif;
	background-color: rgba(255, 255, 255, .85);
	box-shadow: inset 0 0 4px rgba(0, 0, 0, .9), 4px 10px 20px rgba(0, 0, 0, .1);
}

::-webkit-input-placeholder { font-style: italic; }
::-moz-placeholder 					{ font-style: italic; }
:-ms-input-placeholder 			{ font-style: italic; }
:-moz-placeholder 					{ font-style: italic; }

input[type=text]:focus {
	background-color: rgba(255, 255, 255, 1);
	box-shadow: inset 0 0 2px rgba(0, 0, 0, .8), 4px 10px 40px rgba(0, 0, 0, .15);
}

input[type=text]:focus, button[type=submit]:focus {
	outline-color: rgba(255, 255, 255, .1);
}

button[type=submit] {
	cursor: pointer;
	font-weight: 700;
  line-height: 1.375;
	letter-spacing: .04em;
	color: #f7f7f7;
	background-color: rgba(120, 180, 240, .8);
	box-shadow: 4px 10px 20px rgba(0, 0, 0, .1);
	text-shadow: 1px 1px 2px rgba(0, 0, 0, .2);
}

button[type=submit]:hover {
	background-color: rgba(110, 170, 250, .95);
	box-shadow: 4px 10px 40px rgba(0, 0, 0, .15);
}

/* Select styles */
.select-wrap {
  position: relative;
  display: inline-block;
  margin-right: 5px;
  min-width: 120px;
}

.trigger,
.activetrigger {
  position: relative;
  z-index: 5;
  display: block;
  margin-right: 0;
  font-weight: 600;
  color: #393939;
  transition: .1s background-color linear, .1s box-shadow linear;
}

.activetrigger {
  background-color: rgba(255, 255, 255, 1);
	box-shadow: inset 0 0 2px rgba(0, 0, 0, .8), 0 4px 20px rgba(0, 0, 0, .15);
}

.dropcontainer {
	position:absolute;
  top: 90%; left: 0;
  width: 100%;
}

.dropcontainer ul {
  list-style-type: none;
  margin: 0;
  padding: 10px 0 5px;
  border-radius: 4px;
	background-color: rgba(255, 255, 255, 1);
  box-shadow: inset 0 0 2px rgba(0, 0, 0, .8), 4px 10px 40px rgba(0, 0, 0, .15);
}

.dropcontainer ul li:first-child {
	display: none;
}

.dropcontainer ul li a {
  display: block;
  padding: 5px 10px;
  font-weight: 600;
  color: #393939;
  transition: color .2s linear, background-color 0.2s linear .05s;
}

.dropcontainer ul li a:hover {
  color: #f7f7f7;
  background-color: rgba(110, 170, 250, .95);
}


.dropdownhidden {
	display: none;
}

.dropdownvisible {
	height: auto;
}

@media screen and (max-width: 400px) {
  input[type=text] {
    box-sizing: border-box;
    width: 100%;
  }
}
</style>
