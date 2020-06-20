<template>
  <div class="container">
    
    <img alt="Vue logo" v-if="maquina" :src="catImg(maquina.imagem)" >
    <CaJu  @maquina-teste="teste"/>
  </div>
</template>

<script>
// @ is an alias to /src

import CaJu from '@/components/CaJu.vue'
import maquinasJSON from "../components/json/maquinas.json";

export default {
  name: 'Home',
  components: {
   CaJu
  },
  data: function() {
    return {
      maquina: null,
      maquinas : maquinasJSON,
    }
  },
  
  methods: {
    // Triggered when `childToParent` event is emitted by the child.
    teste: function (value) {
      console.log(value);
      this.maquina = this.maquinas[value]
     
    },
    catImg(pic){
       return require('../assets/img/'+ pic);
    }
   },


}
</script>
