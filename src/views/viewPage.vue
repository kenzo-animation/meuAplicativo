<template>
<IonPage>

<IonHeader>
<IonToolbar>
<IonTitle>Visualizar tarefas</IonTitle>

<IonButton color="primary" @click="router.push('/tarefas')">
  Voltar para tarefas
</IonButton>
</IonToolbar>
</IonHeader>

<IonContent class="ion-padding">

<div v-for="(tarefa, index) in tarefas" :key="index">
  {{ tarefa }}
</div>

</IonContent>

</IonPage>
</template>

<script setup lang="ts">

import { ref, onMounted } from "vue";
import { useRouter } from "vue-router";
import {
IonPage,
IonHeader,
IonToolbar,
IonTitle,
IonContent,
IonButton
} from "@ionic/vue";

const router = useRouter();

const tarefas = ref<string[]>([]);

onMounted(() => {

const dados = localStorage.getItem("tarefas");

if(dados){
tarefas.value = JSON.parse(dados);
}

});

</script>