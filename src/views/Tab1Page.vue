<template>
  <ion-page>
    <ion-header>
      <ion-toolbar>
        <ion-title>Galeria de fotos</ion-title>
      </ion-toolbar>
    </ion-header>
    <ion-content :fullscreen="true">
      <ion-header collapse="condense">
      </ion-header>

      <ion-grid>
        <ion-row>
          <ion-col size="2" :key="photo" v-for="photo in photos">
            <ion-img :src="photo.webviewPath"></ion-img>
          </ion-col>    
        </ion-row>
      </ion-grid>

<ion-fab vertical="bottom" horizontal="center" slot="fixed">
  <ion-fab-button>
    <ion-icon :icon="camera" @click="takePhoto()"></ion-icon>
  </ion-fab-button>
</ion-fab>

    </ion-content>
  </ion-page>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import { IonPage, IonHeader, IonToolbar, IonTitle, IonContent } from '@ionic/vue';
import { camera, trash, close} from 'ionicons/icons';
import { usePhotoGallery, UserPhoto} from '@/composable/usePhotoGallery';

export default  defineComponent({
  name: 'Tab1Page',
  components: { IonHeader, IonToolbar, IonTitle, IonContent, IonPage,},
  setup() {
    const { takePhoto, photos } = usePhotoGallery();
    return {
      photos,
      camera,
      trash, 
      close,
      takePhoto
    }
  }
});
</script>