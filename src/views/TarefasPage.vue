<script setup lang="ts">
import { ref } from "vue";
import { useTarefas } from "../composable/useTarefas";
import CardTarefa from "../components/CardTarefa.vue";
import { IonPage, IonHeader, IonToolbar, IonTitle, IonContent, IonList, IonItem, IonInput, IonButton, IonSelect, IonSelectOption, IonLabel } from "@ionic/vue";
const {
  busca,
  filtroAtivo,
  filtradas,
  totalPendentes,
  adicionar,
  remover,
  concluir,
} = useTarefas();
const novaTarefa = ref("");
function adicionarNova() {
  adicionar(novaTarefa.value);
  novaTarefa.value = "";
}
</script>

<template>
  <ion-page>
    <ion-header>
      <ion-toolbar>
        <ion-title>Tarefas</ion-title>
      </ion-toolbar>
    </ion-header>
    <ion-content>
      <ion-list>
        <ion-item>
          <ion-input v-model="novaTarefa" placeholder="Nova tarefa" @keyup.enter="adicionarNova"></ion-input>
          <ion-button slot="end" @click="adicionarNova">Adicionar</ion-button>
        </ion-item>
        <ion-item>
          <ion-input v-model="busca" placeholder="Buscar"></ion-input>
        </ion-item>
        <ion-item>
          <ion-select v-model="filtroAtivo">
            <ion-select-option value="todas">Todas</ion-select-option>
            <ion-select-option value="pendentes">Pendentes</ion-select-option>
            <ion-select-option value="feitas">Feitas</ion-select-option>
          </ion-select>
        </ion-item>
        <ion-item>
          <ion-label>Total pendentes: {{ totalPendentes }}</ion-label>
        </ion-item>
      </ion-list>
      <ion-list>
        <CardTarefa
          v-for="tarefa in filtradas"
          :key="tarefa.id"
          :tarefa="tarefa"
          @remover="remover"
          @concluir="concluir"
        />
      </ion-list>
    </ion-content>
  </ion-page>
</template>

