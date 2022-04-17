<template>
  <div>
  	<h1 :style="{ textDecoration: decoration }">Hello, {{ name }}!</h1>
    <input type="text" v-model="name">
    <br>
    <a :href="link">Link para o curso de VueJS</a>
  </div>
</template>

<script>
  export default {
    data: () => ({
      name: 'Diogo',
      link: 'https://treinamento.vuejsbrasil.org',
      decoration: 'underline'
    })
  }
</script>