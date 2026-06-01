<template>
  <ListaProductos :productos="productosPerifericos" />
</template>
<script setup>
import { productos } from '../../data/productos.js'
import ListaProductos from '../ListaProductos.vue'
import {onMounted, onUnmounted, onActivated, onDeactivated} from 'vue';

const productosPerifericos = productos.filter(
    p => p.categoria === 'Periféricos'
)

onMounted(() => console.log('TabPerifericos — montado'))
onUnmounted(() => console.log('TabPerifericos — desmontado'))
onActivated(() => console.log('TabPerifericos — activado'))
onDeactivated(() => console.log('TabPerifericos — desactivado'))
</script>