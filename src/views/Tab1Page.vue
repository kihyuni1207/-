<template>
  <ion-page>
    <ion-header>
      <ion-toolbar>
        <ion-title>차트</ion-title>
      </ion-toolbar>
    </ion-header>
    <ion-content :fullscreen="true">
      <!-- Line Chart Component -->
      <ion-card class="chart-card">
        <ion-card-header>
          <ion-card-title>라인 차트</ion-card-title>
        </ion-card-header>
        <ion-card-content>
          <ChartComponent />
        </ion-card-content>
      </ion-card>

      <!-- Pie Chart Component -->
      <ion-card class="chart-card">
        <ion-card-header>
          <ion-card-title>파이 차트</ion-card-title>
        </ion-card-header>
        <ion-card-content>
          <ChartComponent2 />
        </ion-card-content>
      </ion-card>

      <!-- Analysis Chart Component -->
      <ion-card class="chart-card">
        <ion-card-header>
          <ion-card-title>분석 차트</ion-card-title>
        </ion-card-header>
        <ion-card-content>
          <ChartComponent3 />
        </ion-card-content>
      </ion-card>
    </ion-content>
  </ion-page>
</template>

<script setup lang="ts">
import {
  IonPage,
  IonContent,
  IonCardTitle,
  IonCardContent,
  IonCard,
  IonCardHeader,
  IonTitle, IonToolbar, IonHeader,
} from '@ionic/vue';
import ChartComponent from '@/components/ChartCom.vue'; // Import your chart component
import ChartComponent2 from '@/components/ChartCom2.vue'; // Import your chart component
import ChartComponent3 from '@/components/ChartCom3.vue'; // Import your chart component

</script>
