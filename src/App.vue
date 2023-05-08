<script setup>
import { ref, computed } from 'vue'

const Descricao = ref(false);
const produtoSelecionado = ref({});
const contador = ref(0);
const totalItem = computed(() => {
  return produtos.value.preco * contador.value
})

const produtos = ref([
  {
    id: 1,
    nome: 'Batom Líquido',
    preco: 29.90,
    descricao: '',
  },
  {
    id: 2,
    nome: 'Paleta De Sombra',
    preco: 59.90,
    descricao: '',
  },
  {
    id: 3,
    nome: 'Deliniador Colorido',
    preco: 11.75,
    descricao: '',
  },
  {
    id: 4,
    nome: 'Blush',
    preco: 19.95,
    descricao: '',
  },
  {
    id: 5,
    nome: 'Pó Compacto',
    preco: 29.90,
    descricao: '',
  },
  {
    id: 6,
    nome: 'Demaquilante',
    preco: 10.00,
    descricao: '',
  },
  {
    id: 7,
    nome: 'Contorno em pó',
    preco: 29.00,
    descricao: '',
  },
  {
    id: 8,
    nome: 'Iluminador',
    preco: 17.99,
    descricao: '',
  },
  {
    id: 9,
    nome: 'Base Líquida',
    preco: 21.50,
    descricao: '',
  },
  {
    id: 10,
    nome: 'Rimel',
    preco: 15.69,
    descricao: '',
  }
]);

const carrinho = ref([
  {

    id: 1,
    nome: 'Batom Líquido',
    preco: 29.90,
    quantidade: 0,
    valorTotal: ''
  },
  {
    id: 2,
    nome: 'Paleta De Sombra',
    preco: 59.90,
    quantidade: 0,
    valorTotal: ''
  },
  {
    id: 3,
    nome: 'Deliniador Colorido',
    preco: 11.75,
    quantidade: 0,
    valorTotal: ''
  },
  {
    id: 4,
    nome: 'Blush',
    preco: 19.95,
    quantidade: 0,
    valorTotal: ''
  },
  {
    id: 5,
    nome: 'Pó Compacto',
    preco: 29.90,
    quantidade: 0,
    valorTotal: ''
  },
  {
    id: 6,
    nome: 'Demaquilante',
    preco: 10.00,
    quantidade: 0,
    valorTotal: ''
  },
  {
    id: 7,
    nome: 'Contorno em pó',
    preco: 29.00,
    quantidade: 0,
    valorTotal: ''
  },
  {
    id: 8,
    nome: 'Iluminador',
    preco: 17.99,
    quantidade: 0,
    valorTotal: ''
  },
  {
    id: 9,
    nome: 'Base Líquida',
    preco: 21.50,
    quantidade: 0,
    valorTotal: ''
  },
  {
    id: 10,
    nome: 'Rimel',
    preco: 15.69,
    quantidade: 0,
    valorTotal: ''
  }
]);

function selecionarProduto(produto) {
  if (produto.id === produtoSelecionado.value.id) {
    Descricao.value = !Descricao.value;
  } else {
    produtoSelecionado.value = produto;
    Descricao.value = true;
  }
};

function incrementarContador(item) {
  carrinho.value[item.id - 1].quantidade += 1;
};

function decrementarContador(item) {

  if (carrinho.value[item.id - 1].quantidade > 0) {
    carrinho.value[item.id - 1].quantidade -= 1;
  };
};


</script>

<template>
  <main>
    <h1>Compras</h1>

    <div class="produtos">
      <div v-for="produto in produtos" :key="produto.id">

        <p class="title">
          {{ produto.nome }}
        </p>


        <p class="quantidade">Quantidade: </p>

        <div class="contador">

          <button class="decrementar" @click="decrementarContador(produto)">-</button>

          {{ carrinho[produto.id - 1].quantidade }}

          <button class="incrementar" @click="incrementarContador(produto)">+</button>

        </div>

        <button class="button-28" @click="selecionarProduto(produto)"> {{ Descricao && produto.id ===
          produtoSelecionado.id ? 'Ocultar Descrição' : 'Mostrar descrição' }}</button>

        <div class="descricao" v-if="Descricao && produto.id === produtoSelecionado.id">{{ produto.descricao }}</div>

        <div v-if="Descricao && produto.id === produtoSelecionado.id">

          <p class="preco">Preço: {{ produto.preco }}R$</p>
        </div>

      </div>
    </div>
  </main>

</template>