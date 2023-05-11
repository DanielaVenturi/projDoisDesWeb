<script setup>

import { ref } from 'vue'


const listaCompras1 = ref([
  {
    id: 1,
    nome: 'Chaveiro do Cascão-Turma Da Mônica',
    preco: 7.90,
    quantidade: 0,
    img: `chavCascao.webp`,
  },
  {
    id: 2,
    nome: 'Chaveiro do Cebolinha-Turma Da Mônica',
    preco: 7.90,
    quantidade: 0,
    img: 'chaveiroCebolinha.webp',
  },
  {
    id: 3,
    nome: 'Chaveiro da Magali-Turma Da Mônica',
    preco: 7.90,
    quantidade: 0,
    img: 'chaveiroMagali.jpg',
  },
  {
    id: 4,
    nome: 'Chaveiro da Mônica-Turma da Mônica',
    preco: 7.90,
    quantidade: 0,
    img: 'ChaveiroMonica.jpg',
  },
  {
    id: 5,
    nome: 'Chaveiro do Mingau-Turma da Mônica',
    preco: 7.90,
    quantidade: 0,
    img:'ChavMingau.webp'
  },
  {
    id: 6,
    nome: 'Chaveiro do Tasco-Turma Da Mônica',
    preco: 7.90,
    quantidade: 0,
    img: 'Chavtasco.jpg'
  },
  
   
])

const carrinhos = ref({
  items: [],
  total: 0,

})

function incrementar(index) {
  listaCompras1.value[index].quantidade++
}
function decrementar(index) {
  if (listaCompras1.value[index].quantidade > 0) {
    listaCompras1.value[index].quantidade--
  }
}

function adicionar(index) {
  if (listaCompras1.value[index].quantidade > 0) {

    carrinhos.value.items.push(
      { ...listaCompras1.value[index], preco: listaCompras1.value[index].quantidade * listaCompras1.value[index].preco }
    );

    carrinhos.value.total = carrinhos.value.total + listaCompras1.value[index].preco * listaCompras1.value[index].quantidade

  }

  

}
</script>

<template>
  <div class="box">

    <div class="item" v-for="(item, index) in listaCompras1" :key="item.id">

      <p>Item: {{ item.nome }}</p>
      <p>Preco: {{ item.preco }}</p>
      <p>ID: {{ item.id }}</p>
      <p>quantidade: {{ item.quantidade }}</p>
      
        <img :src="item.img" >
      

      <div class="botao">

        <button @click="decrementar(index)">-</button>
        <button @click="incrementar(index)">+</button> <br>
        <button @click="adicionar(index)">Adicionar</button>


      </div>
    </div>

  </div>


  <div class="box">

<div class="item" v-for="(item, index) in listaCompras1" :key="item.id">

  <p>Item: {{  item.nome }}</p>
  <p>Preco: {{ item.preco }}</p>
  <p>ID: {{ item.id }}</p>
  <p>quantidade: {{ item.quantidade }}</p>
  
    <img :src="item.img" >
  

  <div class="botao">

    <button @click="decrementar(index)">-</button>
    <button @click="incrementar(index)">+</button> <br>
    <button @click="adicionar(index)">Adicionar</button>


  </div>
</div>

</div>




  <div class="carrinho">

    <div class="item" v-for="item in carrinhos.items">

      <p>Item: {{ item.nome }}</p>
      <p>Preco: {{ item.preco.toFixed(2) }}</p>
      <p>ID: {{ item.id }}</p>
      <p>Quantidade: {{ item.quantidade }}</p>
      <img :src="item.img" >


    </div>
    <p> Total:{{ carrinhos.total.toFixed(2) }}</p>
  </div>
</template>

<style scoped>
.box {
  border-style: double;
  display: grid;
  grid-template-columns: 400px 400px 400px;
}

.item {
  margin-top: 50px;
  border-style: groove;
  margin-right: 25px;
  margin-left: 25px;
  align-items: center;
  margin-bottom: 50px;
  
}

p {
  text-align: center;
}

.botao {
  text-align: center;
  border-style: groove;
  margin-left: 75px;
  margin-right: 75px;
}
img{
  border-style: groove;
  width: 100px;
  text-align: center;
  margin-left: 120px;
  margin-right: 75px;
  
}

</style>