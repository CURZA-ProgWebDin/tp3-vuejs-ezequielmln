<template>
    <p v-if="cargando">Cargando...</p>
    <div ref="box" class="lista">
    <TarjetaProducto v-for="(producto) in productos" :key="producto.id">
        <template #header>
            <h3>{{ producto.nombre }}</h3>
        </template>
        <template #body="{ expandida, toggleExpandir }">
            <p>Id: {{ producto.id }}</p>
            <p>Nombre: {{ producto.nombre }}</p>
            <p v-if="expandida">Categoría: {{ producto.categoria }}</p>
            <p>Precio: {{ producto.precio }}</p>
            <p>Stock: {{ producto.stock }}</p>
            <button @click="toggleExpandir">{{ expandida ? 'Ver menos' : 'Ver más' }}</button>
        </template>
</TarjetaProducto>
</div>
</template>    
<script setup>
import TarjetaProducto from './TarjetaProducto.vue';
import {
  ref,
  useTemplateRef,
  onMounted,
  onUpdated,
  onBeforeUnmount
} from 'vue';

const props = defineProps({
    productos: {
        type: Array,
        required: true
    }
});

const box = useTemplateRef('box');

function esperar(ms) {
  return new Promise(resolve => setTimeout(resolve, ms))
}
const cargando = ref(false) ;

let timer = null;

async function CargarProductos() {
  cargando.value = true;
  await esperar(800);
  console.log('Productos cargados');
  cargando.value = false;
}

onMounted(() => {
  CargarProductos();

  timer = setInterval(() => {
    CargarProductos();
  }, 30000);
});

onUpdated(() => {
  if (box.value) {
    box.value.scrollTop = box.value.scrollHeight;
  }
});

onBeforeUnmount(() => {
  clearInterval(timer)
  console.log('ListaProductos desmontado — polling detenido')
})
</script>
<style scoped>
.lista {
  max-height: 400px;
  max-width: 600px;
  overflow-y: auto;
  background-color: #e6eeee;
  padding: 10px;
}
</style>