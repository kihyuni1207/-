<template>
  <ion-page>
    <ion-header>
      <ion-toolbar>
        <ion-title>인사이트</ion-title>
      </ion-toolbar>
    </ion-header>
    <ion-content>
      <div class="cont-wrap">
        <div class="kb-dashboard-wrap">
          <div class="kb-cont">
            <ion-card>
              <ion-card-header>
                <ion-card-title>보안 위험 감지 현황</ion-card-title>
              </ion-card-header>
              <ion-card-content>
                <ion-list>
                  <ion-item>
                    <ion-label style=" font-weight: bold;color: #c7c7c7">총</ion-label>
                    <ion-note slot="end" style="font-size: 25px; font-weight: bold;color: #fff">10</ion-note>
                  </ion-item>
                  <ion-item>
                    <ion-label style=" font-weight: bold;color: #c7c7c7">클라우드 이벤트 이상</ion-label>
                    <ion-note slot="end" style="font-size: 25px; font-weight: bold;color: #fff">5</ion-note>
                  </ion-item>
                  <ion-item>
                    <ion-label style=" font-weight: bold;color: #c7c7c7">VPC 네트워크 이상</ion-label>
                    <ion-note slot="end" style="font-size: 25px; font-weight: bold;color: #fff">3</ion-note>
                  </ion-item>
                  <ion-item>
                    <ion-label style=" font-weight: bold;color: #c7c7c7">EC2 인스턴스 이상</ion-label>
                    <ion-note slot="end" style="font-size: 25px; font-weight: bold;color: #fff">2</ion-note>
                  </ion-item>
                </ion-list>
              </ion-card-content>
            </ion-card>
            <ion-card>
              <ion-card-header>
                <ion-card-title>EKS 최적화 요약</ion-card-title>
              </ion-card-header>
              <ion-card-content>
                <div id="eksOptimizationChart" style="height: 300px;"></div>
                <ion-list>
                  <ion-item v-for="(category, index) in categoryItems" :key="index">
                    <ion-label style=" font-weight: bold;color: #c7c7c7">{{ category.name }}</ion-label>
                    <ion-note slot="end" style="font-size: 25px; font-weight: bold;color: #fff">{{ category.optimizedCount }} / {{ category.totalCount }}</ion-note>
                  </ion-item>
                </ion-list>
              </ion-card-content>
            </ion-card>
            <ion-card>
              <ion-card-header>
                <ion-card-title>EC2 인스턴스 최적화 요약</ion-card-title>
              </ion-card-header>
              <ion-card-content>
                <ion-list>
                  <ion-item>
                    <ion-label style=" font-weight: bold;color: #c7c7c7">EC2 인스턴스 최적화 수</ion-label>
                    <ion-note slot="end" style="font-size: 25px; font-weight: bold;color: #fff">8 / 12</ion-note>
                  </ion-item>
                  <ion-item>
                    <ion-label style=" font-weight: bold;color: #c7c7c7">비용 절감률</ion-label>
                    <ion-note slot="end" style="font-size: 25px; font-weight: bold;color: #fff">
                      <ion-icon :name="'arrow-up'" />
                      25<em>%</em>
                    </ion-note>
                  </ion-item>
                </ion-list>
              </ion-card-content>
            </ion-card>
          </div>
        </div>
      </div>
    </ion-content>
  </ion-page>
</template>

<script setup lang="ts">
import { ref, onMounted } from 'vue';
import Highcharts from 'highcharts';
import {
  IonPage,
  IonContent,
  IonList,
  IonItem,
  IonCardTitle,
  IonCardContent,
  IonCard,
  IonIcon,
  IonNote,
  IonLabel,
  IonCardHeader,
  IonTitle, IonToolbar, IonHeader,
} from '@ionic/vue';



const chartOptions = {
  chart: {
    type: 'column',
    backgroundColor: 'transparent',
  },
  title: {
    text: '',
  },
  xAxis: {
    categories: ['2022', '2023'],
    labels: {
      style: {
        color: '#fff', // Set the label text color to white
      },
    },
  },
  yAxis: {
    title: {
      text: '',
    },
    labels: {
      style: {
        color: '#fff', // Set the label text color to white
      },
    },
  },
  series: [
    {
      name: 'Optimized Values',
      data: [8, 12],
      color: '#fff',
    },
  ],
  credits: {
    enabled: false,
  },
  dataLabels: {
    enabled: false,
  },
  legend: {
    itemStyle: {
      color: '#fff',
    },
  },
  tooltip: {
    style: {
      color: '#4d4d4d',
    },
  },
};

const isLoading = ref(false);

// Your EKS optimization data
const categoryItems = ref([
  {
    name: 'POD 추천',
    optimizedCount: 8,
    totalCount: 12,
  },
  {
    name: 'HPA 추천',
    optimizedCount: 12,
    totalCount: 18,
  },
]);

onMounted(() => {
  Highcharts.chart('eksOptimizationChart', chartOptions);
});

</script>
