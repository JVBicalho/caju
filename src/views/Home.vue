<template>
  <div class="row h-100"  >
    
      <div class="col-12 ">
        <div class="row pt-4" v-if="maquina">
          <div class="pull-left col-6">
            <img alt="Vue logo"  :src="catImg(maquina.imagem)" style="filter: drop-shadow(0 6px 10px rgba(0,0,0,.5));" >

          </div>
          <div class="col-6">
            <h3 class="text-justify">{{ maquina.name}}</h3>
          </div>
        </div>

        <CaJu  @maquina-teste="teste" />
      </div>
      
  
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
