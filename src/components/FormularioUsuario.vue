<template>
  <div class="fondo">
    <h1 class="Bienvenido">Bienvenido, completa el siguiente formulario</h1>
    <form @submit.prevent="validarFormulario">
      <div>
        <label class="nombre">Nombre:</label>
        <input class="campo" type="text" v-model="nombre" :class="{ 'campo-invalido': errores.nombre }">
        <p v-if="errores.nombre" class="mensaje-error">{{ errores.nombre }}</p>
      </div>
      <div>
        <label class="apellido">Apellido:</label>
        <input class="campo" type="text" v-model="apellido" :class="{ 'campo-invalido': errores.apellido }">
        <p v-if="errores.apellido" class="mensaje-error">{{ errores.apellido }}</p>
      </div>
      <div>
        <label class="edad">Edad:</label>
        <input class="Edad" type="number" v-model="edad" :class="{ 'campo-invalido': errores.edad }">
        <p v-if="errores.edad" class="mensaje-error">{{ errores.edad }}</p>
      </div>
      <div>
        <label class="Genero">Género:</label>
        <select class="genero" v-model="genero" :class="{ 'campo-invalido': errores.genero }">
          <option value="">Selecciona un género</option>
          <option value="masculino">Masculino</option>
          <option value="femenino">Femenino</option>
          <option value="otros">Prefiero no especificar</option>
        </select>
        <p v-if="errores.genero" class="mensaje-error">{{ errores.genero }}</p>
      </div>
      <div>
        <label class="numero">Teléfono:</label>
        <input class="campo" type="tel" v-model="telefono" :class="{ 'campo-invalido': errores.telefono }">
        <p v-if="errores.telefono" class="mensaje-error">{{ errores.telefono }}</p>
      </div>
      <button class="boton" type="submit">Enviar</button>
    </form>
  </div>
</template>

<script setup  lang="ts">
import { ref } from 'vue';
const nombre = ref('');
    const apellido = ref('');
    const edad = ref();
    const genero = ref('');
    const telefono = ref('');
    const errores = ref({});


      const  validarFormulario = () => {
      errores.value = {};
      let esValido = true;
      let palabrasApellido = apellido.value.toLowerCase().split(' ');
      let nombres = nombre.value.toLowerCase().split(' ');

  
      if (nombre.value.length > 18) {
        errores.value.nombre = 'El nombre no puede tener más de 18 caracteres';
        esValido = false;
      }
      
      for (let nombre of nombres) {
       if (palabrasApellido.includes(nombre)) {
       errores.value.apellido = 'El apellido no puede repetirse en el campo nombres';
       esValido = false;
       break;
       }
      } 

      if (!telefono.value || telefono.value.length > 10) {
        errores.value.telefono = 'El número de teléfono no puede tener más de 10 dígitos';
        esValido = false;
      }

      if (!apellido.value || apellido.value.length > 18) {
        errores.value.apellido = 'El apellido no puede tener más de 18 caracteres';
        esValido = false;
      }

      if (nombre.value === apellido.value) {
        errores.value.nombre = 'El nombre y apellido no pueden ser iguales';
        errores.value.apellido = 'El nombre y apellido no pueden ser iguales';
        esValido = false;
      }

      if (!edad.value || edad.value <= 0 || edad.value > 60) {
        errores.value.edad = 'Selecciona tu edad, debe estar entre 0 y 60';
        esValido = false;
      }

      if (!genero.value) {
        errores.value.genero = 'Selecciona un genero';
        esValido = false;
      }

      return esValido;
    }
</script>

<style scoped>

.fondo {
position: relative;
padding: 30px 30px;
background: #fff;
border-radius: 10px;
}
.campo-invalido {
  border-color: rgb(247, 247, 247);
  font-family: 'Itim', cursive;
}
.mensaje-error {
  color: red;
  font-family: 'Itim', cursive;
}
.Bienvenido {
  color:rgb(22, 10, 249);
  font-family: 'McLaren', sans-serif;
  font-family: 'Outfit', sans-serif;
  line-height: 1.7;
  text-align:left;
}

.nombre {
  color:black;
  font-family: 'Itim', cursive;
}
.apellido {
  color:black;
  font-family: 'Itim', cursive;
}
.edad {
  color:black;
  font-family: 'Itim', cursive;
}
.Edad {
  color:black;
  font-family: 'Itim', cursive;
}
.Genero {
  color:black;
  font-family: 'Itim', cursive;
}
.numero {
  color:black;
  font-family: 'Itim', cursive;
}
.campo {
width: 180px;
padding: 5px;
background-color: white;
border-radius: 8px;
box-shadow: 0px 0px 1px rgba(0, 0, 0, 0.1);
font-family: 'Itim', cursive;
}
.Edad {
width: 180px;
padding: 5px;
background-color: white;
border-radius: 8px;
box-shadow: 0px 0px 1px rgba(0, 0, 0, 0.1);
font-family: 'Itim', cursive;
}
.genero {
width: 180px;
padding: 5px;
background-color: white;
border-radius: 8px;
box-shadow: 0px 0px 1px rgba(0, 0, 0, 0.1);
font-family: 'Itim', cursive;
}
.boton {
width: 100%;
padding: 10px;
border: none;
border-radius: 4px;
background-color: #ff00bf;
color: white;
cursor: pointer;
border-radius: 8px;
}
</style>