<script>
export default{
  data(){
    return{
      nome : 'Vinicius Acordi Soethe',
      idade: '21',
      cpf: '000000000000',
      nacionalidade: 'Brasileiro',
      likes: 0
    }
  },
  methods:{
    addLike(){
      this.likes= this.likes +1
    },
    remLike(){
      this.likes= this.likes -1
    }
  }
}
</script>
<script setup>

</script>

<template>
  <h1>Olá Vue</h1>
  <h2>nome:{{nome}}</h2>
  <h2>idade:{{idade}}</h2>
  <h2>cpf:{{cpf}}</h2>
  <h2>likes:{{likes}}</h2>
  <button v-on:click="addLike">Like</button>
  <button v-on:click="remLike">Dilike</button>
  <input type="text" v-model="nome"/>
</template>

<style>

#app {
  max-width: 1280px;
  margin: 0 auto;
  padding: 2rem;

  font-weight: normal;
}

/* header {
  line-height: 1.5;
}

.logo {
  display: block;
  margin: 0 auto 2rem;
}

a,
.green {
  text-decoration: none;
  color: hsla(160, 100%, 37%, 1);
  transition: 0.4s;
}

@media (hover: hover) {
  a:hover {
    background-color: hsla(160, 100%, 37%, 0.2);
  }
}

@media (min-width: 1024px) {
  body {
    display: flex;
    place-items: center;
  }

  #app {
    display: grid;
    grid-template-columns: 1fr 1fr;
    padding: 0 2rem;
  }

  header {
    display: flex;
    place-items: center;
    padding-right: calc(var(--section-gap) / 2);
  }

  header .wrapper {
    display: flex;
    place-items: flex-start;
    flex-wrap: wrap;
  }

  .logo {
    margin: 0 2rem 0 0;
  }
} */
</style> 
