<script setup>
import {
  IonPage,
  IonHeader,
  IonToolbar,
  IonTitle,
  IonContent,
  IonInput,
  IonButtons,
  IonButton
} from '@ionic/vue'

import { ref, watch } from 'vue'

const nome = ref('')
const mensagem = ref('')

watch(nome, (novo) => {
  mensagem.value = `Nome atualizado: ${novo}`
})
</script>

<template>
  <ion-page>
    <ion-header>
      <ion-toolbar color="primary">

        <ion-buttons slot="start">
          <ion-button router-link="/home">Home</ion-button>
        </ion-buttons>

        <ion-title>Perfil</ion-title>
      </ion-toolbar>
    </ion-header>

    <ion-content class="ion-padding">
      <h2>Perfil</h2>

      <ion-input v-model="nome" placeholder="Digite seu nome" />

      <p>{{ mensagem }}</p>
    </ion-content>
  </ion-page>
</template>