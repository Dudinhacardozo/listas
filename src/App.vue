<script setup>

import { ref } from 'vue'


const listaCompras = ref([
{
        id: 1,
        nome: ' calça wide leg',
        preco: 99.90,
        quantidade: 0,

    },
    {
        id: 2,
        nome: 'Shorts Saia',
        preco: 59.90,
        quantidade: 0,
    },
    {
        id: 3,
        nome: 'Blusa',
        preco: 29.90,
        quantidade: 0,
    },
    {
        id: 4,
        nome: 'Saia',
        preco: 45.56,
        quantidade: 0,
    },
    {
        id: 5,
        nome: 'Biquíne',
        preco: 60.99,
        quantidade: 0,
    },
    {
        id: 6,
        nome: 'Casaco De Moletom',
        preco: 200.00,
        quantidade: 0,
    },
    {
        id: 7,
        nome: 'Jaqueta Jeans',
        preco: 299.90,
        quantidade: 0,
    },
    {
        id: 8,
        nome: 'Vestido',
        preco: 79.90,
        quantidade: 0,
    },
    {
        id: 9,
        nome: 'Blusa De Tricô',
        preco: 29.90,
        quantidade: 0,
    },
    {
        id: 10,
        nome: 'Cropped',
        preco: 59.90,
        quantidade: 0,
    }
])

const carrinhos = ref({
  items: [],
  total: 0,
    
})

function incrementar(index) {
    listaCompras.value[index].quantidade++
  }
  function decrementar(index) {
    if(listaCompras.value[index].quantidade > 0){
      listaCompras.value[index].quantidade--
    }
  }
  
  function adicionar(index) {
    if(listaCompras.value[index].quantidade > 0){
      
      carrinhos.value.items.push(
        {...listaCompras.value[index], preco: listaCompras.value[index].quantidade * listaCompras.value[index].preco}
      );
      
      carrinhos.value.total = carrinhos.value.total + listaCompras.value[index].preco * listaCompras.value[index].quantidade
       
    }
    
  }
</script>

<template>
  <h1 class="titulo">DK</h1>
  <h2 class="titulo">Duda Kardozo</h2>
        
  <div class="produtos">
    <ul>
      <li class="lista" v-for="(item, index) in listaCompras" :key="item.id">
        <p>Item: {{ item.nome }}</p>
        <p>Preco: {{ item.preco }}</p>
        <p>ID: {{ item.id }}</p>
        <p>quantidade: {{ item.quantidade }}</p>
        <button @click="incrementar(index)">+</button>
        <button @click="decrementar(index)">-</button>
        <button @click="adicionar(index)">Adicionar</button>
      </li>
    </ul>
    <hr>
  </div>

  <div class="carrinhoC">
  <ul>

    <li v-for="item in carrinhos.items">
        <p>Item: {{ item.nome }}</p>
        <p>Preco: {{ item.preco.toFixed(2) }}</p>
        <p>ID: {{ item.id }}</p>
        <p>Quantidade: {{ item.quantidade }}</p>

       
    </li>

    <p> Total:{{ carrinhos.total.toFixed(2) }}</p>
  </ul>
  </div>
</template>

<style scoped>

.titulo{
  text-align: center;
  font-family: Garamond	;
  color: hotpink;
}

li{
 display: grid;
  align-items:center;
  margin-bottom: 30px;
  grid-template-columns: 1fr ;
}

</style>