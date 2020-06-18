<template>
  <div class="row ">
    <div class="col-12">
      <form @submit.prevent>
        <section v-if="step == 1">
          <div class="form-group">
            <label for="item">Escolha a Maquina:</label>
            <select
              class="form-control"
              v-model="form.maquina"
              id="item"
              aria-describedby="itemHelp"
            >
              <option
                v-for="maquina in maquinas"
                v-bind:value="maquina.index"
                v-bind:key="maquina.id"
                >{{ maquina.name }}</option
              >
            </select>

            <small id="itemHelp" class="form-text "></small>
          </div>
        </section>
        <section v-if="step == 2">
          <div class="form-group">
            <label for="item">Crédito ou Débito ?</label>
            <div class="form-check">
              <input
                class="form-check-input"
                type="radio"
                name="exampleRadios"
                id="exampleRadios1"
                v-bind:value="false"
                v-model="form.credito"
                checked
              />
              <label class="form-check-label" for="exampleRadios1">
                Débito.
              </label>
            </div>
            <div class="form-check">
              <input
                class="form-check-input"
                type="radio"
                name="exampleRadios"
                id="exampleRadios2"
                v-bind:value="true"
                v-model="form.credito"
              />
              <label class="form-check-label" for="exampleRadios2">
                Crédito.
              </label>
            </div>

           

            <small id="itemHelp" class="form-text "></small>
          </div>
        </section>
        <div v-show="form.credito == true">
          <section v-if="step == 3">
            <div class="form-group">
              <label for="item">Escolha seu plano de recebimento:</label>
              <select
                class="form-control"
                v-model="form.planoRecebimento"
                id="item"
                aria-describedby="itemHelp"
              >
                <option
                  v-for="plano in maquinas[form.maquina].planosRecebimento"
                  v-bind:value="plano.taxa"
                  v-bind:key="plano.index"
                  >{{ plano.name }}</option
                >
              </select>

              <small id="itemHelp" class="form-text "></small>
            </div>
          </section>
          <section v-if="step == 4">
            <div class="form-group">
              <label for="item">Escolha o parcelamento :</label>
              <select
                class="form-control"
                v-model="form.txParcelamento"
                id="item"
                aria-describedby="itemHelp"
              >
                <option
                  v-for="taxa in maquinas[form.maquina].txParcelamento"
                  v-bind:value="taxa.taxa"
                  v-bind:key="taxa.index"
                  >{{ taxa.name }}</option
                >
              </select>

              <small id="itemHelp" class="form-text "></small>
            </div>
          </section>
          <section v-if="step == 5">
            <div class="form-group">
              <label for="#valor">Digite o valor :</label>
              <input
                class="form-control"
                id="valor"
                type="text"
                placeholder="R$ 100,00"
                v-model="form.valor"
              />
            </div>
          </section>
        </div>
        <div v-show="form.credito == false">
            <section v-if="step == 3">
            <div class="form-group">
              <label for="#valor">Digite o valor :</label>
              <input
                class="form-control"
                id="valor"
                type="text"
                placeholder="R$ 100,00"
                v-model="form.valor"
              />
            </div>
          </section>
        </div>
      </form>
      <div>
        
        <button
          v-if="step < 5 && form.credito == true|| form.credito ==false && step < 3"
          class="btn btn-primary col-12 mb-1"
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
                 -->
        <button
          v-else-if="step == 5 && form.credito == true"
          class="btn btn-success col-12 "
          @click.prevent="calcularTaxaCredito()"
        >
          Calcular Taxa De Credito
        </button>
        <button
          v-else-if="step == 3 && form.credito == false"
          class="btn btn-success col-12 "
          @click.prevent="calcularTaxaDebito()"
        >
          Calcular Taxa de Debito
        </button>
        <button
          v-if="step != 1 && step != 4"
          class="btn btn-outline-primary col-12"
          @click.prevent="prevStep()"
        >
          Anterior
        </button>
      </div>
    </div>
  </div>
</template>
<script>
import maquinasJSON from "./json/maquinas.json";
export default {
  name: "CaJu",

  data: function() {
    return {
      maquinas: maquinasJSON,
      step: 1,
      form: {
        maquina: null,
        planoRecebimento: null,
        txParcelamento: null,
        valor: null,
        credito: false,
      },
      itemPrice: null,
      result: [],
    };
  },
  methods: {
    prevStep() {
        if (this.step == 1) {
            return
        }
      this.step--;
      console.log(this.step);
    },
    nextStep() {
      this.step++;
      console.log(this.step);
    },
    calcularTaxaCredito() {
      var taxa;
      var self = this;
      var valor = self.form.valor.replace(",", ".");
      var txR =self.form.planoRecebimento;
      var txP = self.form.txParcelamento;
      taxa = (valor * (txP / 100)) +(valor * (txR / 100));
      console.log(taxa);
    },
    calcularTaxaDebito() {
      var taxa;
      var self = this;
      var valor = self.form.valor.replace(",", ".");
      // var txR =self.form.planoRecebimento;
      var txD = self.maquinas[self.form.maquina].txDebito;
      taxa = valor * (txD / 100);
      console.log(taxa);
    },
  },
};
</script>
