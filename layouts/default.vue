<template>
    <v-app>
        <Cabecalho />
        <v-main>
            <v-container>
                <slot></slot>
            </v-container>
        </v-main>
        <MenuLateral></MenuLateral>
    </v-app>
</template>

<script setup lang="ts">
import Cabecalho from '../components/layout/Cabecalho.vue'
import MenuLateral from '../components/layout/MenuLateral.vue'
// const components = {Cabecalho};
</script>