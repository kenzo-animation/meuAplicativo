<script setup lang="ts">
import { IonCard, IonCardContent, IonItem, IonIcon, IonLabel, IonButton } from "@ionic/vue";
import { checkmarkCircle, ellipseOutline, trashOutline } from "ionicons/icons";

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
          :icon="props.tarefa.feita ? checkmarkCircle : ellipseOutline"
          :color="props.tarefa.feita ? 'success' : 'medium'"
          @click="emit('concluir', props.tarefa.id)"
        />
        <IonLabel
          :style="props.tarefa.feita ? 'text-decoration:line-through' : ''"
        >
          {{ props.tarefa.texto }}
        </IonLabel>
        <div class="ion-padding-start">
          <IonButton
            fill="outline"
            color="primary"
            @click="emit('concluir', props.tarefa.id)"
          >
            {{ props.tarefa.feita ? 'Reabrir' : 'Finalizar' }}
          </IonButton>
          <IonButton
            fill="clear"
            color="danger"
            @click="emit('remover', props.tarefa.id)"
          >
            <IonIcon :icon="trashOutline" /> Excluir
          </IonButton>
        </div>
      </IonItem>
    </IonCardContent>
  </IonCard>
</template>
