<script setup>

import { ref } from 'vue'


const listaCompras = ref([
  {
    id: 1,
    nome: ' calça wide leg',
    preco: 99.90,
    quantidade: 0,
    img: 'https://img.ltwebstatic.com/images3_pi/2022/08/25/166142019213c1ca5f3c9a7a4b59488850dc31a422_thumbnail_600x.webp'


  },
  {
    id: 2,
    nome: 'Shorts Saia',
    preco: 59.90,
    quantidade: 0,
    img: 'https://img.ltwebstatic.com/images3_pi/2023/01/10/167334501585fe3335178b651b0fafe559c1f5401d_thumbnail_600x.webp'
  },
  {
    id: 3,
    nome: 'Blusa',
    preco: 29.90,
    quantidade: 0,
    img: 'https://img.ltwebstatic.com/images3_pi/2022/03/15/164731417132b7c016689436c20bc68a03ff72b17d_thumbnail_600x.webp'
  },
  {
    id: 4,
    nome: 'Saia',
    preco: 45.56,
    quantidade: 0,
    img: 'https://img.ltwebstatic.com/images3_pi/2022/09/26/1664182171f34a240e0599cac87e2feaa03aed0cfe_thumbnail_600x.webp'
  },
  {
    id: 5,
    nome: 'Biquíne',
    preco: 60.99,
    quantidade: 0,
    img: 'https://img.ltwebstatic.com/images3_pi/2023/04/11/16812019219d911997118f4e1377432c026e1d9afd_thumbnail_600x.webp'
  },
  {
    id: 6,
    nome: 'Casaco De Moletom',
    preco: 200.00,
    quantidade: 0,
    img: 'https://img.ltwebstatic.com/images3_pi/2021/08/03/1627980422b033c91e2fa51ba21a29517569abb6f4_thumbnail_600x.webp'
  },
  {
    id: 7,
    nome: 'Jaqueta Jeans',
    preco: 299.90,
    quantidade: 0,
    img: 'https://img.ltwebstatic.com/images3_pi/2021/12/09/1639033059c637e89ce453d21864aa7295228fa64f_thumbnail_600x.webp'
  },
  {
    id: 8,
    nome: 'Vestido',
    preco: 79.90,
    quantidade: 0,
    img: 'https://img.ltwebstatic.com/images3_pi/2021/11/20/1637377278b97c6f27914719cadbb1e74df1edd22b_thumbnail_600x.webp'
  },
  {
    id: 9,
    nome: 'Blusa De Tricô',
    preco: 29.90,
    quantidade: 0,
    img: 'https://img.ltwebstatic.com/gspCenter/goodsImage/2023/4/28/6308007670_1058940/4922c8e7-5df8-4829-9526-722ce6ad8633/DF843AF79A3FABF2F07FB480D9AD188A_thumbnail_600x.jpg'

  },
  {
    id: 10,
    nome: 'Cropped',
    preco: 59.90,
    quantidade: 0,
    img: 'https://img.ltwebstatic.com/images3_pi/2022/04/21/1650525391687692f083d26327773cb93308cdf381_thumbnail_600x.webp'
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
  if (listaCompras.value[index].quantidade > 0) {
    listaCompras.value[index].quantidade--
  }
}

function adicionar(index) {
  if (listaCompras.value[index].quantidade > 0) {

    carrinhos.value.items.push(
      { ...listaCompras.value[index], preco: listaCompras.value[index].quantidade * listaCompras.value[index].preco }
    );

    carrinhos.value.total = carrinhos.value.total + listaCompras.value[index].preco * listaCompras.value[index].quantidade

  }

}
</script>

<template>
  <h1 class="titulo">DK</h1>
  <h2 class="titulo">Duda Kardozo</h2>

  <div class="produtos">
      <div class="lista" v-for="(item, index) in listaCompras" :key="item.id">
        <p>Item: {{ item.nome }}</p>
        <p>Preco: {{ item.preco }}</p>
        <p>ID: {{ item.id }}</p>
        <p>quantidade: {{ item.quantidade }}</p>
        <img class="imagem" :src="item.img" />
        <div class="acoes">
          <button @click="incrementar(index)">+</button>
          <button @click="decrementar(index)">-</button>
          <button @click="adicionar(index)">Adicionar</button>
        </div>
      </div>
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
.titulo {
  text-align: center;
  font-family: Garamond;
  background: linear-gradient(to top right, #ff99ff 0%, #ffffff 99%);
  color: #C71585;
  font-family: bookman old style;

}

.produtos {
  display: grid;
  align-items: center;
  grid-template-columns: 1fr 1fr;
  color:rgb(46, 3, 39);
  font-family: Clarendon Condensed;
}

.lista {
  margin: 10px 30px;
  background: linear-gradient(to top right, #ff99ff 0%, #ffffff 99%);
  border-radius: 20px;
  padding: 30px;
  height: 500px;
}

.lista p {
  margin: 0;
}

.lista .acoes {
  display: flex;
  margin-bottom: 20px;
}

.imagem {
  text-align: center;
  width: 30%;
  margin: 0 auto;
  display: block;
  max-width: 60%;
  max-height: 60%;
  /* margin-bottom: 180px; */
  -moz-box-shadow: 15px 10px 20px #c27dab;
  -webkit-box-shadow: 20px 20px 20px #b670abbe;
  border-radius: 70%;
}
</style>