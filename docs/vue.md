# <i class="fab fa-vuejs"></i> Vue
***
### Playground
<vuep template="#example"></vuep>

<script v-pre type="text/x-template" id="example">
<style>
  .main {
    color: #fff;
  }
  .text {
    color: #4fc08d;
  }
</style>

<template>
  <div class="main">
    <h2> Do you even <span class="text">{{ name }}</span>?</h2>
    <h2>Features</h2>
    <ul>
      <li v-for="text in features">{{ text }}</li>
    </ul>
  </div>
</template>

<script>
  module.exports = {
    data () {
      return {
        name: 'Vue',
        features: [
          'Single File Component',
          'Babel for ES6/JSX/UMD/CommonJS',
          'Scoped style',
          'Customizable JavaScript scope'
        ]
      }
    }
  }
</script>
</script>