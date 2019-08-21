<template>
  <ion-card v-if="info">
    <ion-card-header>
      <ion-card-subtitle>{{info['places'][0]['place name']}}</ion-card-subtitle>
      <ion-card-title>{{info['post code']}}</ion-card-title>
    </ion-card-header>
    <ion-card-content>
      <b>Estado:</b> {{info['places'][0]['state']}}<br>
      <b>Abreviado:</b> {{info['places'][0]['state abbreviation']}}
    </ion-card-content>
  </ion-card>
</template>
<script>
export default{
  name:'InfoCoposve',
  props:["info"]
}
</script>