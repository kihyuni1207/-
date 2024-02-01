<template>
  <ion-page>
    <ion-tabs>
      <ion-router-outlet></ion-router-outlet>
      <ion-tab-bar slot="bottom">
        <ion-tab-button tab="tab1" href="/tabs/tab1">
          <ion-icon aria-hidden="true" :icon="triangle" />
          <ion-label>인사이트</ion-label>
        </ion-tab-button>

        <ion-tab-button tab="tab2" href="/tabs/tab2">
          <ion-icon aria-hidden="true" :icon="ellipse" />
          <ion-label>사진</ion-label>
        </ion-tab-button>

        <ion-tab-button tab="tab3" href="/tabs/tab3">
          <ion-icon :icon="square" />
          <ion-label>알람</ion-label>
        </ion-tab-button>

        <ion-tab-button tab="tab4" href="/tabs/tab4">
          <ion-icon aria-hidden="true" :icon="aperture" />
          <ion-label>교보생명 인사이트 화면</ion-label>
        </ion-tab-button>

      </ion-tab-bar>
    </ion-tabs>
  </ion-page>
</template>

<script setup lang="ts">
import { IonTabBar, IonTabButton, IonTabs, IonLabel, IonIcon, IonPage, IonRouterOutlet } from '@ionic/vue';
import {aperture, ellipse, square, triangle} from 'ionicons/icons';
</script>
