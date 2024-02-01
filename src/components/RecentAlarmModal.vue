<template>
  <ion-page>
    <ion-header>
      <ion-toolbar>
        <ion-title>알람 앱</ion-title>
      </ion-toolbar>
    </ion-header>

    <ion-content>
      <ion-list>
        <ion-item v-for="alarm in alarms" :key="alarm.id">
          <ion-label>
            {{ alarm.title }}
            <p>{{ alarm.time }}</p>
          </ion-label>
          <ion-button @click="editAlarm(alarm)">수정</ion-button>
          <ion-button @click="deleteAlarm(alarm.id)">삭제</ion-button>
        </ion-item>
      </ion-list>

      <ion-button @click="setAlarm">알람 설정</ion-button>
    </ion-content>

    <!-- 모달 다이얼로그 -->
    <ion-modal :is-open="showModal">
      <ion-content class="ion-text-center">
        <ion-card>
          <ion-card-header>
            <ion-card-title>{{ modalTitle }}</ion-card-title>
          </ion-card-header>
          <ion-card-content>
            {{ modalContent }}
          </ion-card-content>
        </ion-card>
        <ion-button @click="closeModal" class="ion-margin">닫기</ion-button>
      </ion-content>
    </ion-modal>
  </ion-page>
</template>

<script lang="ts">
import { defineComponent, ref, onMounted, watch } from 'vue';
import { Plugins } from '@capacitor/core';
import {
  IonContent,
  IonHeader,
  IonPage,
  IonTitle,
  IonToolbar,
  IonLabel,
  IonButton,
  IonItem,
  IonList,
  IonModal,
  IonCard,
  IonCardTitle,
  IonCardHeader,
  IonCardContent,
} from '@ionic/vue';

const { LocalNotifications } = Plugins;

export default defineComponent({
  components: {
    IonContent,
    IonHeader,
    IonPage,
    IonTitle,
    IonToolbar,
    IonLabel,
    IonButton,
    IonItem,
    IonList,
    IonModal,
    IonCard,
    IonCardTitle,
    IonCardHeader,
    IonCardContent,
  },

  setup() {
    interface AlarmType {
      id: number;
      title: string;
      time: string;
    }

    // Create a ref to store alarms as a reactive object
    const alarms = ref<AlarmType[]>([]);
    const showModal = ref(false);
    const modalTitle = ref('');
    const modalContent = ref('');

    const loadAlarms = () => {
      const savedAlarms = JSON.parse(localStorage.getItem('alarms') || '[]');
      alarms.value = savedAlarms;
    };

    const setAlarm = async () => {
      try {
        const alarm = {
          id: Date.now(),
          title: '새로운 알람',
          time: new Date('2023-10-31T08:00:00').toISOString(),
        };
        alarms.value.push(alarm);

        // The watch function will save the alarms to localStorage
        // So, no need to save it here

        showModal.value = true;
        modalTitle.value = '알람 설정 완료';
        modalContent.value = '알람이 설정되었습니다.';

        setTimeout(() => {
          closeModal();
        }, 2000);
      } catch (error) {
        console.error('알람 설정 중 오류 발생:', error);
      }
    };

    const deleteAlarm = (id) => {
      try {
        alarms.value = alarms.value.filter((alarm) => alarm.id !== id);

        showModal.value = true;
        modalTitle.value = '알람 삭제 완료';
        modalContent.value = '알람이 삭제되었습니다.';

        setTimeout(() => {
          closeModal();
        }, 2000);
      } catch (error) {
        console.error('알람 삭제 중 오류 발생:', error);
      }
    };

    const editAlarm = (alarm) => {
      try {
        const updatedAlarm = { ...alarm };
        const newTitle = prompt('새로운 알람 제목', updatedAlarm.title);
        if (newTitle !== null) {
          updatedAlarm.title = newTitle;
          const newTime = prompt('새로운 알람 시간', updatedAlarm.time);
          if (newTime !== null) {
            updatedAlarm.time = newTime;
            alarms.value = alarms.value.map((a) =>
                a.id === updatedAlarm.id ? updatedAlarm : a
            );

            showModal.value = true;
            modalTitle.value = '알람 수정 완료';
            modalContent.value = '알람이 수정되었습니다.';

            setTimeout(() => {
              closeModal();
            }, 1500);
          }
        }
      } catch (error) {
        console.error('알람 수정 중 오류 발생:', error);
      }
    };

    const closeModal = () => {
      showModal.value = false;
    };

    // Watch for changes in alarms and save to localStorage
    watch(alarms, (newAlarms) => {
      localStorage.setItem('alarms', JSON.stringify(newAlarms));
    });

    onMounted(() => {
      loadAlarms();
    });

    return {
      alarms,
      setAlarm,
      deleteAlarm,
      editAlarm,
      showModal,
      modalTitle,
      modalContent,
      closeModal,
    };
  },
});
</script>
