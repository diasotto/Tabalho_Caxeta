<script setup>
import {
  IonPage,
  IonHeader,
  IonToolbar,
  IonTitle,
  IonContent,
  IonButton,
  IonButtons,
  IonBackButton
} from '@ionic/vue'

import { useRoute } from 'vue-router'
import { computed } from 'vue'
import { eventos } from '../data/events'

const route = useRoute()

const evento = computed(() =>
  eventos.find(e => e.id == route.params.id)
)

const toggleFavorito = () => {
  if (evento.value) evento.value.favorito = !evento.value.favorito
}
</script>

<template>
  <ion-page>
    <ion-header>
      <ion-toolbar color="primary">

        <ion-buttons slot="start">
          <ion-back-button default-href="/eventos" />
        </ion-buttons>

        <ion-title>{{ evento?.titulo }}</ion-title>
      </ion-toolbar>
    </ion-header>

    <ion-content class="ion-padding" v-if="evento">
      <h1>{{ evento.titulo }}</h1>

      <p>{{ evento.descricao }}</p>

      <p>📍 {{ evento.local }}</p>
      <p>📅 {{ evento.data }}</p>

      <ion-button expand="block" @click="toggleFavorito">
        {{ evento.favorito ? 'Remover dos favoritos' : 'Favoritar' }}
      </ion-button>
    </ion-content>
  </ion-page>
</template>