<template>
    <slot name="header"></slot>
    <slot name="body" :expandida="expandida" :toggleExpandir="toggleExpandir"></slot>
    <slot name="footer"><span>Sin acciones disponibles</span></slot>
</template>
<script setup>
import { ref } from 'vue';

const expandida = ref(false);

const toggleExpandir = () =>{ 
    expandida.value = !expandida.value;
};

</script>