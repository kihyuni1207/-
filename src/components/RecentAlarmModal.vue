<template>
  <ion-page>
    <!-- 헤더 영역 -->
    <ion-header>
      <ion-toolbar>
        <ion-title>알람 앱</ion-title>
      </ion-toolbar>
    </ion-header>

    <!-- 알람 목록 표시 영역 -->
    <ion-content>
      <ion-list>
        <ion-item v-for="alarm in alarms" :key="alarm.id">
          <ion-label>
            <!-- 알람 제목 및 시간 표시 -->
            <h2>{{ alarm.title }}</h2>
            <p>{{ formatTime(alarm.time) }}</p>
          </ion-label>
          <ion-button @click="editAlarm(alarm)">수정</ion-button>
          <ion-button @click="deleteAlarm(alarm.id)">삭제</ion-button>
        </ion-item>
      </ion-list>
      <!-- 알람 설정 버튼 -->
      <ion-button style="margin-top: 60px" @click="setNewAlarm" expand="full">알람 설정</ion-button>
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
        <ion-button @click="closeModal" expand="full">닫기</ion-button>
      </ion-content>
    </ion-modal>
  </ion-page>
</template>

<script lang="ts">
import { defineComponent, onMounted, ref, watch } from 'vue';
import {
  IonButton,
  IonCard,
  IonCardContent,
  IonCardHeader,
  IonCardTitle,
  IonContent,
  IonHeader,
  IonItem,
  IonLabel,
  IonList,
  IonModal,
  IonPage,
  IonTitle,
  IonToolbar,
} from '@ionic/vue';

export default defineComponent({
  components: {
    IonButton,
    IonCard,
    IonCardContent,
    IonCardHeader,
    IonCardTitle,
    IonContent,
    IonHeader,
    IonItem,
    IonLabel,
    IonList,
    IonModal,
    IonPage,
    IonTitle,
    IonToolbar,
  },

  setup() {
    interface AlarmType {
      id: number;
      title: string;
      time: string;
    }

    // 알람 목록 및 모달 상태
    const alarms = ref<AlarmType[]>([]);
    const showModal = ref(false);
    const modalTitle = ref('');
    const modalContent = ref('');

    // 알람 목록 불러오기
    const loadAlarms = () => {
      alarms.value = JSON.parse(localStorage.getItem('alarms') || '[]');
    };

    // 새로운 알람 설정
    const setNewAlarm = async () => {
      try {
        const alarm = {
          id: Date.now(),
          title: '새로운 알람',
          time: new Date('2023-10-31T08:00:00').toISOString(),
        };

        alarms.value.push(alarm);

        showModal.value = true;
        modalTitle.value = '알람 설정 완료';
        modalContent.value = '알람이 설정되었습니다.';

        setTimeout(() => {
          closeModal();
        }, 1500);
      } catch (error) {
        console.error('알람 설정 중 오류 발생:', error);
      }
    };

    // 알람 삭제
    const deleteAlarm = (id: number) => {
      try {
        alarms.value = alarms.value.filter((alarm) => alarm.id !== id);

        showModal.value = true;
        modalTitle.value = '알람 삭제 완료';
        modalContent.value = '알람이 삭제되었습니다.';

        setTimeout(() => {
          closeModal();
        }, 1500);
      } catch (error) {
        console.error('알람 삭제 중 오류 발생:', error);
      }
    };

    // 알람 수정
    const editAlarm = (alarm: any) => {
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

    // 모달 닫기
    const closeModal = () => {
      showModal.value = false;
    };

    // 시간 형식 변경
    const formatTime = (time: string) => {
      return new Date(time).toLocaleTimeString();
    };

    // 알람 목록 변경 감시 및 저장
    watch(alarms, (newAlarms) => {
      localStorage.setItem('alarms', JSON.stringify(newAlarms));
    });

    onMounted(() => {
      loadAlarms();
    });

    return {
      alarms,
      setNewAlarm,
      deleteAlarm,
      editAlarm,
      showModal,
      modalTitle,
      modalContent,
      closeModal,
      formatTime,
    };
  },
});
</script>
