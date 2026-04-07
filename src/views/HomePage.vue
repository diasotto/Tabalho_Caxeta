<script setup>
import {
  IonPage,
  IonContent,
  IonButton
} from '@ionic/vue'
</script>

<template>
  <ion-page>
    <ion-content class="home">
      <div class="container">
        <h1>🎉 SmartEvent</h1>
        <p>Descubra eventos incríveis na sua cidade</p>

        <ion-button expand="block" shape="round" router-link="/eventos">
          Explorar Eventos
        </ion-button>

        <ion-button expand="block" shape="round" fill="outline" router-link="/favoritos">
          Favoritos
        </ion-button>

        <ion-button expand="block" fill="clear" router-link="/perfil">
          Perfil
        </ion-button>
      </div>
    </ion-content>
  </ion-page>
</template>

<style scoped>
.home {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100%;
}

.container {
  text-align: center;
  width: 100%;
}

h1 {
  font-size: 28px;
  margin-bottom: 10px;
}

p {
  opacity: 0.7;
  margin-bottom: 30px;
}
</style>