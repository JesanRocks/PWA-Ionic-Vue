<template>
  <div class="ion-page">
    
    <ion-header>
        <ion-toolbar color="primary">
          <ion-title>Coposve</ion-title>
        </ion-toolbar>
    </ion-header>
    <ion-content class="ion-padding">
        <BuscarCoposve v-on:obtenerCodigo="infoCodigo"/>
        <InfoCoposve v-bind:info="info"/>
        <ClearInfoCoposve v-bind:info="info" v-on:clear-info="clearInfo"/>
    </ion-content>    
  </div>
</template>

<script>
import BuscarCoposve from "../components/BuscarCoposve";
import InfoCoposve from "../components/InfoCoposve";
import ClearInfoCoposve from "../components/ClearInfoCoposve";
export default {
  name: 'home',
  components: { BuscarCoposve, InfoCoposve, ClearInfoCoposve },
  data(){
    return{
     info:null
    }
  },
  methods:{
    async infoCodigo(codigo){
        const res = await fetch(`https://api.zippopotam.us/us/${codigo}`);
        if (res.status == 404) {
            this.showAlert();
        }
        this.info = await res.json();
    },
    clearInfo() {
        this.info=null;
    },
    showAlert() {
        return this.$ionic.alertController
        .create({
          header: "Codigo Postal Invalido",
          message: "¡Por favor, ingrese un Codigo Postal de EE.UU. válido!",
          buttons: ["OK"]
        })
        .then(a => a.present());
    }
  }
}
</script>
