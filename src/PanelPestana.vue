<template>
 <!-- sin keepalive, los componentes se montan y desmontan cada vez que se cambia de pestaña-->
  <h2>Sin keepAlive</h2>
  <div>
    <button @click="tabActivoSin = TabTodos">Todos</button>
    <button @click="tabActivoSin = TabElectronica">Electrónica</button>
    <button @click="tabActivoSin = TabPerifericos">Periféricos</button>
  </div>
  <component :is="tabActivoSin" />
 <!-- con keepalive, los componentes se montan una sola vez y se mantienen en memoria, aunque no estén activos-->
 <!-- Los momentos donde se use cada uno depende de cuando queramos utilizar las caracteristicas de cada uno, como por ejemplo, con keepalive es común su uso en formularios, componentes sin en páginas de login--> 
  <h2>Con keepAlive</h2>
    <div>
    <button @click="tabActivoCon = TabTodos">Todos</button>
    <button @click="tabActivoCon = TabElectronica">Electrónica</button>
    <button @click="tabActivoCon = TabPerifericos">Periféricos</button>
  </div>
  <KeepAlive>
    <component :is="tabActivoCon" />
  </KeepAlive>
</template>
<script setup>
import { ref } from 'vue';
import TabTodos from './components/tabs/TabTodos.vue';
import TabElectronica from './components/tabs/TabElectronica.vue';
import TabPerifericos from './components/tabs/TabPerifericos.vue';

const tabActivoSin = ref(TabTodos);
const tabActivoCon = ref(TabTodos);
</script>