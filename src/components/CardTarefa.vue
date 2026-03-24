<script setup lang="ts">
import { IonCard, IonCardContent, IonItem, IonIcon, IonLabel, IonButton } from "@ionic/vue";

interface Tarefa {
  id: number;
  texto: string;
  feita: boolean;
}
const props = defineProps<{ tarefa: Tarefa }>();
const emit = defineEmits<{
  remover: [id: number];
  concluir: [id: number];
}>();
</script>
<template>
  <IonCard>
    <IonCardContent>
      <IonItem lines="none">
        <IonIcon
          slot="start"
          :icon="props.tarefa.feita ? 'checkmark-circle' : 'ellipse-outline'"
          :color="props.tarefa.feita ? 'success' : 'medium'"
          @click="emit('concluir', props.tarefa.id)"
        />
        <IonLabel
          :style="props.tarefa.feita ? 'text-decoration:linethrough' : ''"
        >
          {{ props.tarefa.texto }}
        </IonLabel>
        <IonButton
          slot="end"
          fill="clear"
          color="danger"
          @click="emit('remover', props.tarefa.id)"
        >
          <IonIcon :icon="'trash-outline'" />
        </IonButton>
      </IonItem>
    </IonCardContent>
  </IonCard>
</template>
