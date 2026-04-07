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

import { computed } from 'vue'
import { eventos } from '../data/events'
import EventCard from '../components/EventCard.vue'

const favoritos = computed(() =>
  eventos.filter(e => e.favorito)
)
</script>

<template>
  <ion-page>
    <ion-header>
      <ion-toolbar color="primary">

        <ion-buttons slot="start">
          <ion-button router-link="/home">Home</ion-button>
        </ion-buttons>

        <ion-title>Favoritos</ion-title>
      </ion-toolbar>
    </ion-header>

    <ion-content>
      <div v-if="favoritos.length === 0" class="empty">
        ⭐ Nenhum favorito ainda
      </div>

      <event-card
        v-for="evento in favoritos"
        :key="evento.id"
        :evento="evento"
      />
    </ion-content>
  </ion-page>
</template>