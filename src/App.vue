<template>
  <div id="app">
    <FormularioUsuario />
  </div>
</template>

<script>
import FormularioUsuario from './components/FormularioUsuario.vue'

export default {
  components: {
    FormularioUsuario
  }
}
</script>


<style>
body {
  background: rgb(206,145,255);
  background: linear-gradient(90deg, rgba(206,145,255,1) 0%, rgba(180,166,245,1) 3%, rgba(250,181,252,1) 35%, rgba(0,212,255,1) 100%);
  margin: 0 auto;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  line-height: 3.4;
  width: 400px;
}

#app {
  display: flex;
  justify-content: center;
  align-items: center;
  height:100vh;
}

@media (max-width: 600px) {
  .form {
    padding: 10px;
  }
}
</style>
