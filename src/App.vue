<script setup>

import { ref } from 'vue'

const listaCompras = ref([
{ 
        id: 1,
        nome: 'Blush',
        preco: 19.50,
        quantidade: 0,
    },
    {
        id: 2,
        nome: 'Base Líquida',
        preco: 22.90,
        quantidade: 0,
    },
    {
        id: 3,
        nome: 'Delíniador Líquido',
        preco: 19.00,
        quantidade: 0,
    },
    {
        id: 4,
        nome: 'Máscara Para Cílios Preta',
        preco: 20.99,
        quantidade: 0,
    },
    {
        id: 5,
        nome: 'Corretivo Líquido',
        preco: 19.90,
        quantidade: 0,
    },
    {
        id: 6,
        nome: 'Hidratante Lábial',
        preco: 10.90,
        quantidade: 0,
    },
    {
        id: 7,
        nome: 'Paleta De Sombras',
        preco: 90.55,
        quantidade: 0,
    },
    {
        id: 8,
        nome: 'Kit De Pinceis',
        preco: 59.90,
        quantidade: 0,
    },
    {
        id: 9,
        nome: 'Batom Líquido',
        preco: 22.00,
        quantidade: 0,
    },
    {
        id: 10,
        nome: 'Pó Facial',
        preco: 24.90,
        quantidade: 0,
    }
])

const carrinhos = ref([
{
        id: 10,
        nome: 'Blush',
        preco: 19.55,
        quantidade: 0,
    }
])

function incrementar(index) {
    listaCompras.value[index].quantidade++
  }
  function descrementar(index) {
    listaCompras.value[index].quantidade--
  }
  
  function adicionar(index) {
    carrinhos.value.push(listaCompras.value)
    carrinhos.value = ''
  }
  
</script>

<template>
  <div class="produtos">
    <ul>
      <li class="lista" v-for="(item, index) in listaCompras" :key="item.id">
        <p>Item: {{ item.nome }}</p>
        <p>Preco: {{ item.preco }}</p>
        <p>ID: {{ item.id }}</p>
        <p>quantidade: {{ item.quantidade }}</p>
        <button @click="incrementar(index)">+</button>
        <button @click="descrementar(index)">-</button>
        <button @click="adicionar">Adicionar</button>
      </li>
    </ul>
    <hr>
    <li v-for="item in carrinhos">
        <p>Item: {{ item.nome }}</p>
        <p>Preco: {{ item.preco }}</p>
        <p>ID: {{ item.id }}</p>
    </li>
  </div>
</template>

<style scoped></style>