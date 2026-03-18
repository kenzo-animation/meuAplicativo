<template>
  <IonPage>
    <IonHeader>
      <IonToolbar>
        <IonTitle>Contador</IonTitle>

        <ion-button color="dark" @click="router.push('/tarefas')">
          tarefas
        </ion-button>
      </IonToolbar>
    </IonHeader>

    <IonContent class="ion-padding">
      <h2>Valor atual: {{ contador }}</h2>

      <IonButton expand="block" @click="incrementar"> Incrementar </IonButton>

      <IonButton expand="block" color="danger" @click="tirar">
        tire 1
      </IonButton>

      <IonButton expand="block" color="danger" @click="resetar">
        resetar
      </IonButton>

      <IonButton expand="block" color="success" @click="multiplicar">
        multiplique o valor por click
      </IonButton>

    </IonContent>
  </IonPage>
</template>

<script setup lang="ts">
import { ref } from "vue";
import { useRouter } from "vue-router";
import {
  IonPage,
  IonHeader,
  IonToolbar,
  IonTitle,
  IonContent,
  IonButton,
} from "@ionic/vue";

const router = useRouter();

const contador = ref(0);
const incremento = ref(1);

const incrementar = () => {
  contador.value += incremento.value;
};

const tirar = () => {
  contador.value -= incremento.value;
};

const resetar = () => {
  contador.value = 0;
  incremento.value = 1;
};

const multiplicar = () => {
  incremento.value *= 2;
};
</script>
