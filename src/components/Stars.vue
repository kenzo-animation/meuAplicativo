<template>
  <h1>Componente Stars</h1>
  <ion-but  ton
    v-for="(value, indice) in 5"
    :class="amarelo: indice < total"
    :key="indice"
  ></ion-button>
</template>

<script setup>
import { defineProps } from "vue";

import { IonButton } from "@ionic/vue";

const props = defineProps({
  total: { type: Number, default: 0 },
});
</script>
