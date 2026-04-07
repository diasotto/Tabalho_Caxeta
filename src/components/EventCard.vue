<script setup>
import {
  IonCard,
  IonCardHeader,
  IonCardTitle,
  IonCardContent,
  IonButton,
  IonIcon
} from '@ionic/vue'

import { heart, heartOutline } from 'ionicons/icons'

const props = defineProps({
  evento: Object
})

const emit = defineEmits(['favoritar', 'abrir'])
</script>

<template>
  <ion-card class="card" @click="$emit('abrir', evento.id)">
    <ion-card-header>
      <ion-card-title>{{ evento.titulo }}</ion-card-title>
    </ion-card-header>

    <ion-card-content>
      <p>📍 {{ evento.local }}</p>
      <p>📅 {{ evento.data }}</p>

      <ion-button expand="block" shape="round" @click.stop="$emit('favoritar', evento.id)">
        <ion-icon :icon="evento.favorito ? heart : heartOutline" slot="start" />
        {{ evento.favorito ? 'Favoritado' : 'Favoritar' }}
      </ion-button>
    </ion-card-content>
  </ion-card>
</template>

<style scoped>
.card {
  margin: 14px;
  border-radius: 20px;
  box-shadow: 0 8px 20px rgba(0,0,0,0.08);
  transition: 0.2s;
}

.card:hover {
  transform: scale(1.02);
}

p {
  margin: 6px 0;
  font-size: 14px;
}
</style>