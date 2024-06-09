<template>
    <v-app-bar :elevation="2">
        <v-app-bar-nav-icon variant="text" @click.stop="mostrarBarraLateral = !mostrarBarraLateral"></v-app-bar-nav-icon>
        <v-app-bar-title>Application Bar</v-app-bar-title>
    </v-app-bar>
</template>
<script setup lang="ts">
import { ref, inject, watch } from 'vue'
import {EventBusFactory, eventNames} from '../../infra/eventBus'

const eventBus = EventBusFactory.getEventBus();
const mostrarBarraLateral = ref(true);
watch(mostrarBarraLateral, (_, novoValor) => {
    eventBus.publish(eventNames.mostrarBarraLateral, novoValor)
})

</script>