<template>
  <ion-page>
    <div class="overlay" v-if="isLoading"></div>
    <ion-content class="ion-padding">
      <img src="../images/logo-kyobo.svg" style="width: 200px;">
      <div></div>
      <div class="login-container">
        <ion-item>
          <ion-input v-model="username" type="text" placeholder="Username"></ion-input>
        </ion-item>
        <ion-item style="margin-top: 30px; margin-bottom: 50px;">
          <ion-input v-model="password" type="password" placeholder="Password" @keyup.enter="login"></ion-input>
          <!-- @keyup.enter 이벤트를 사용하여 Enter 키를 눌렀을 때 login 함수를 호출 -->
        </ion-item>
        <ion-button expand="full" shape="round" @click="login" :disabled="isLoading" class="login-button">Login</ion-button>
        <ion-spinner style="margin-top:-100px;font-weight: bold;color: #00a9ff;" v-if="isLoading"></ion-spinner>
      </div>

      <!-- 로그인 성공 및 실패 모달 -->
      <ion-modal v-if="showModal" :is-open="showModal" @ionModalDidDismiss="showModal = false" style="margin-top: 350px;">
        <div class="modal-content">
          <ion-text class="modal-text">{{ modalMessage }}</ion-text>
          <ion-button expand="full" @click="closeModal" class="modal-button">OK</ion-button>
        </div>
      </ion-modal>

    </ion-content>
  </ion-page>
</template>

<script lang="ts">
import { defineComponent, ref } from 'vue';
import { IonInput, IonItem, IonPage, IonToolbar, IonHeader, IonTitle, IonButton, IonContent, IonSpinner, IonImg, IonModal, IonText } from '@ionic/vue';
import router from '@/router'; // Vue Router 설정 가져오기

export default defineComponent({
  components: {
    IonInput,
    IonImg,
    IonItem,
    IonPage,
    IonToolbar,
    IonHeader,
    IonTitle,
    IonButton,
    IonContent,
    IonSpinner,
    IonModal,
    IonText,
  },
  setup() {
    const username = ref('');
    const password = ref('');
    const isLoading = ref(false);
    const showModal = ref(false);
    const modalMessage = ref('');

    const login = async () => {
      isLoading.value = true;
      setTimeout(() => {
        if (username.value === 'admin' && password.value === 'okestro2018') {
          modalMessage.value = '로그인 성공';
          showModal.value = true;
          localStorage.setItem('loggedIn', 'true');
          localStorage.setItem('username', username.value);
          router.push('/tabs/tab1');
        } else {
          modalMessage.value = '로그인 실패';
          showModal.value = true;
        }
        isLoading.value = false;
      }, 2000);
    };

    const closeModal = () => {
      showModal.value = false;
    };

    return {
      username,
      password,
      login,
      isLoading,
      showModal,
      modalMessage,
      closeModal,
    };
  },
});
</script>

<style scoped>
.overlay {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-color: rgba(0, 0, 0, 0.5); /* Adjust the opacity as needed */
  z-index: 999; /* Ensure the overlay is on top of other content */
  display: flex;
  justify-content: center;
  align-items: center;
  pointer-events: none; /* Allow interactions with elements underneath */
}

.login-container {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  margin-top: 30vh;
}

.login-button {
  --ion-color-base: #fff;
  --ion-color-contrast: #007BFF;
  --ion-background-color: #007BFF;
  --ion-border-radius: 20px;
  --ion-padding-start: 20px;
  --ion-padding-end: 20px;
}


/* 모달 스타일 */
ion-modal {
  --ion-background-color: rgba(0, 0, 0, 0.7);
  --ion-border-radius: 20px;
  --ion-padding: 20px;
  --ion-max-width: 80%;
  display: flex;
  justify-content: center;
  align-items: center;
}

.modal-content {
  background-color: #fff;
  text-align: center;
  padding: 20px;
  border-radius: 20px;
}

.modal-text {
  color: #007BFF;
  font-weight: bold;
  font-size: 20px;
  margin-bottom: 20px;
}


.modal-button {
  --ion-color-base: #fff;
  --ion-color-contrast: #007BFF;
  --ion-background-color: #007BFF;
  --ion-border-radius: 20px;
  font-weight: bold;
}


</style>
