<template>
  <div id="app">
    <div id="posicion-logotipo"><img id="logotipo" alt="Vue logo" src="./assets/logo1.jpeg"></div>
    <HelloWorld msg=""/>
    <EtiquetaComponent @onTagsChange="handleOnTagsChange"></EtiquetaComponent>
    
  </div>  
</template>

<script>
import HelloWorld from './components/HelloWorld.vue';
//Importación del componente etiqueta
import EtiquetaComponent from './components/EtiquetaComponent.vue';



export default {
  name: 'App',
  components: {
    HelloWorld,
    EtiquetaComponent,
    
  },
  methods:{
    handleOnTagsChange(tags){
      console.log(tags);
    }
  }
}
</script>

<style>
#logotipo{
  width: 250px;
  height: 320px;
  margin: auto;
  align-items: center;
}
  
</style>
