<template>
    <v-navigation-drawer v-model="mostrarBarraLateral" :location="$vuetify.display.mobile ? 'bottom' : undefined" temporary>
        <v-list nav>
            <div v-for="menu in menuItems" :value="menu.title" :title="menu.title" :key="menu.title">
                <v-list-group :value="menu.title" v-if="menu.children">
                    <template v-slot:activator="{ props }">
                        <v-list-item v-bind="props" :title="menu.title"></v-list-item>
                    </template>
                    <v-list-item v-for="child in menu.children" :title="child.title"></v-list-item>
                </v-list-group>

                <v-list-item v-else :value="menu.title" :title="menu.title">
                </v-list-item>
            </div>
        </v-list>
    </v-navigation-drawer>
</template>
<script setup lang="ts">
import { ref } from 'vue'
import {EventBusFactory, eventNames} from '../../infra/eventBus'

const eventBus = EventBusFactory.getEventBus();
eventBus.subscribe(eventNames.mostrarBarraLateral, (novoValor:boolean) => {
  mostrarBarraLateral.value = novoValor
})

const mostrarBarraLateral = ref(false)

interface MenuItem {
  title: string,
  value: string,
  children?: MenuItem[] | null
}

const items: MenuItem[] = [];

for (let index = 0; index < 5; index++) {
  let child = null;
  if (index % 2 == 0)
    child = [{ title: 'Sub menu', value: 'Sub' }]
  items.push({ title: `Menu ${index}`, value: `${index}`, children: child });
}

const menuItems = ref(items);

</script>