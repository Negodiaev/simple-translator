<template>
  <h3 class="translated-text">{{ translatedText }}</h3>
</template>

<script>
  export default {
    name: 'translate-output',
    props: ['translatedText']
  }
</script>

<style>
  .translated-text {
    display: inline-block;
    min-height: 49px;
    border-bottom: 2px solid peachpuff;
    font-size: 36px;
    text-transform: capitalize;
    color: peachpuff;
  }

  @media screen and (max-width: 400px) {
    .translated-text {
      min-height: auto;
      border-bottom: 0;
      font-size: 32px;
    }
  }
</style>
