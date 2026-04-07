<script setup>
import {
  IonPage,
  IonHeader,
  IonToolbar,
  IonTitle,
  IonContent,
  IonButtons,
  IonButton
} from '@ionic/vue'

import { ref } from 'vue'
import { useRouter } from 'vue-router'
import { eventos } from '../data/events'
import EventCard from '../components/EventCard.vue'

const router = useRouter()
const lista = ref(eventos)

const toggleFavorito = (id) => {
  const e = lista.value.find(ev => ev.id === id)
  if (e) e.favorito = !e.favorito
}

const abrirDetalhe = (id) => {
  router.push(`/eventos/${id}`)
}
</script>

<template>
  <ion-page>
    <ion-header>
      <ion-toolbar color="primary">
        <ion-buttons slot="start">
          <ion-button router-link="/home">Home</ion-button>
        </ion-buttons>

        <ion-title>Eventos</ion-title>
      </ion-toolbar>
    </ion-header>

    <ion-content>
      <event-card
        v-for="evento in lista"
        :key="evento.id"
        :evento="evento"
        @favoritar="toggleFavorito"
        @abrir="abrirDetalhe"
      />
    </ion-content>
  </ion-page>
</template>