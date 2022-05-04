<template>
 <div>
  <Fondo_movil/>
  <Calculadora_prueba />
   </div> 
</template>

<script>
import Calculadora_prueba from './components/Calculadora_prueba';
import Fondo_movil from './components/Fondo_movil';
export default {
  name: 'App',
  components: {
    Calculadora_prueba,
    Fondo_movil,
  }
}
</script>

<style>


</style>
