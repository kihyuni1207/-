<template>
  <ion-page>
    <ion-header>
      <ion-toolbar>
        <ion-title>알람</ion-title>
      </ion-toolbar>
    </ion-header>
    <ion-content :fullscreen="true">
      <ion-header collapse="condense">
        <ion-toolbar>
          <ion-title size="large">알람</ion-title>
        </ion-toolbar>
      </ion-header>

      <Alarm/>

    </ion-content>
  </ion-page>
</template>

<script setup lang="ts">
import { IonPage, IonHeader, IonToolbar, IonTitle, IonContent } from '@ionic/vue';

import Alarm from '@/components/RecentAlarmModal.vue'; // Import your chart component

</script>
