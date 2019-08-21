<template>
  <ion-button color="light" expand="block" v-if="info" @click="$emit('clear-info')">Vaciar</ion-button>
</template>
<script>
export default{
  name:'ClearInfoCoposve',
  props:["info"]
}
</script>