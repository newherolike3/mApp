<template>
  <ion-page>
    <ion-header>
      <ion-toolbar>
        <ion-title>หน้าหลัก</ion-title>
      </ion-toolbar>
    </ion-header>
    <ion-content :fullscreen="true">

      <ion-grid>
        <ion-row>
          <ion-col>
            <ion-button>button 1</ion-button>
          </ion-col>
          <ion-col>
            <ion-button color="danger" size="small">button 2</ion-button>
          </ion-col>
        </ion-row>
        <ion-row>
          <ion-col>
            <ion-button color="success" size="large">button 3</ion-button>
          </ion-col>
          <ion-col>
            <ion-button shape="round" fill="outline">button 4</ion-button>
          </ion-col>
        </ion-row>
      </ion-grid>
      
      
      
      
      

    </ion-content>
  </ion-page>
</template>

<script lang="ts">
import { IonPage, IonHeader, IonToolbar, IonTitle, IonContent, IonButton, IonGrid, IonRow, IonCol } from '@ionic/vue';

export default  {
  name: 'Tab1',
  components: { IonHeader, IonToolbar, IonTitle, IonContent, IonPage, IonButton, IonGrid, IonRow, IonCol }
}
</script>