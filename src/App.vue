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
    imagem:"batomliquido.png"
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
<div v-for="(produto,index) in produtos " :key="index" > {{ produto.id }} {{ produto.nome }}
    <img :src="produto.imagem" alt="" width="200">
    <button class="btn-adicionar" @click="incrementar">+</button>
    <img :src="batomliquido.png" alt="" width="25" class="btn-deletar" @click="resetar">
    <button class="btn-decrmentar" @click="decrementar">-</button>
    <p>Quantidade de produtos:{{ quantidade }}</p>
    </div>
  

</template>