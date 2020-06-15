<template>
    <div class="row " style="padding-bottom:3em" >
        <div class="">
            <form @submit.prevent >
                <section v-if="step == 1">
                    <div class="form-group">
                        <label for="item">Escolha a Maquina:</label>
                            <select class="form-control" 
                            v-model="form.item"
                            id="item"
                            aria-describedby="itemHelp"
                            >
                                <option v-for="maquina in maquinas" v-bind:value="maquina.index" v-bind:key="maquina.id" >{{ maquina.name }}</option>
                                
                                
                                
                            </select>
                        
                        <small id="itemHelp" class="form-text "
                            ></small
                        >
                    </div>
                </section>
                <section v-if="step == 2">
                  
                </section>
                <section v-if="step == 3">
                  
                </section>
                <section v-if="step == 4">

                 
                    
                </section>
        
                
            </form>
            <div>
                 <button
                    v-if="step != 1 && step !=4"
                    class="btn btn-warning float-left"
                    @click.prevent="prevStep()"
                >
                    Anterior
                </button>
                <button v-if="step < 3"
                    class="btn btn-warning float-right"
                    @click.prevent="nextStep()"
                >
                    Proximo
                </button>
                
                <!-- <button v-else-if="step == 3"
                    class="btn btn-warning float-right"
                    @click.prevent="calcularColeta()"
                >
                    Calcular
                </button>
                <button v-else-if="step ==  4"
                    class="btn btn-warning col-12 "
                    @click.prevent="resetColeta()"
                >
                    Calcular Outro Recurso
                </button> -->
            </div>
        </div>
    </div>
</template>
<script>
import maquinasJSON from './json/maquinas.json'
export default {
  name: 'CaJu',
  
    data: function() {
        return {
            maquinas:maquinasJSON,
            step: 1,
            form: {
                item: null,
                tier:null,
                valor:null,
                
            },
            itemPrice:null,
            result:[],
            
        };
    },
  methods: {
        prevStep() {
            this.step--;
            console.log(this.step);
        },
        nextStep() {
            this.step++;
            console.log(this.step);
        },
  }
}
</script>