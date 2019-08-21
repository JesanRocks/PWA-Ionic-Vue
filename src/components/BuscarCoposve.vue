<template>
  <ion-grid>
    <form @submit="onSubmit">
      <ion-col>
        <ion-item>
          <ion-label>Codigo postal:</ion-label>
          <ion-input :value="codigo" @input="codigo = $event.target.value" placeholder="Ingresa tu codigo Postal" name="codigo"></ion-input>
        </ion-item>
      </ion-col>
      <ion-col>
        <ion-button type="submit" color="primary" expand="block">Buscar</ion-button>
      </ion-col>
    </form>
  </ion-grid>
</template>

<script>
export default {
  name: 'BuscarCoposve',
  data(){
    return{
      codigo:""
    };
  },
  methods:{
    onSubmit(e) {
      e.preventDefault();
      // Codigo Postal Regex
      const codigoValido = /(^\d{5}$)|(^\d{5}-\d{4}$)/.test(this.codigo);
      // Prueba para validar codigo

      if (!codigoValido) {
        this.showAlert();
        this.codigo = "";
      }else{
        this.$emit("obtenerCodigo", this.codigo);
        this.codigo = "";
      }
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
