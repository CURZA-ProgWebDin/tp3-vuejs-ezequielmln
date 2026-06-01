<template>
  <ListaProductos :productos="productosElectronica" />
</template>
<script setup>
import { productos } from '../../data/productos.js'
import ListaProductos from '../ListaProductos.vue'
import {onMounted, onUnmounted, onActivated, onDeactivated} from 'vue';

const productosElectronica = productos.filter(
    p => p.categoria === 'Electrónica'
)

onMounted(() => console.log('TabElectronica — montado'))
onUnmounted(() => console.log('TabElectronica — desmontado'))
onActivated(() => console.log('TabElectronica — activado'))
onDeactivated(() => console.log('TabElectronica — desactivado'))
</script>