<template>
    <v-app-bar :elevation="2">
        <v-app-bar-nav-icon variant="text" @click.stop="mostrarBarraLateral = !mostrarBarraLateral"></v-app-bar-nav-icon>
        <v-app-bar-title>Application Bar</v-app-bar-title>
    </v-app-bar>
</template>
<script setup lang="ts">
import { ref } from 'vue'

const mostrarBarraLateral = ref(false)

</script>