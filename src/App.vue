<script>
export default {
  data() {
    return {
      nome: "Vinicius Acordi Soethe",
      idade: "21",
      cpf: "000000000000",
      nacionalidade: "Brasileiro",
      likes: 0,
      valor: 6.0,
      frutas: ["Pera", "Uva", "Laranja", "Uva"],
      novocarro: {
        id: "KD",
        desc: "Kia picanto",
      },
      carros: [
        {
          id: 0,
          desc: "Uno",
        },
        {
          id: 1,
          desc: "Gol",
        },
        {
          id: 2,
          desc: "Jetta",
        },
      ],
    };
  },
  methods: {
    addLike() {
      this.likes = this.likes + 1;
    },
    remLike() {
      this.likes = this.likes - 1;
    },
    getLikes() {
      return this.likes;
    },
    adicionarCarro() {
      this.carros.push(this.novocarro);
      this.novocarro = {};
    },
    removerCarro(carro) {
      const pos = this.carros.findIndex((c) => c === carro);
      this.carros.splice(pos, 1);
    },
  },
  computed: {
    meta1() {
      return this.likes === 5;
    },
    getLikes2() {
      return this.likes;
    },
    icms() {
      //foma 1
      // if (this.valor < 5) return this.valor * 0.3;
      // else if (this.valor < 6) return this.valor * 0.25;
      // else return this.valor * 0.2;
      let porcent = 0.2;
      if (this.valor < 5) porcent = 0.3;
      else if (this.valor < 6) porcent = 0.25;
      return this.valor * porcent;
    },
  },
};
</script>
<script setup></script>

<template>
  <h1>Olá Vue</h1>
  <h2>nome:{{ nome }}</h2>
  <h2>idade:{{ idade }}</h2>
  <h2>cpf:{{ cpf }}</h2>
  <h2>likes:{{ likes }}</h2>
  <button v-on:click="addLike">Like</button>
  <button v-on:click="remLike">Dilike</button>

  <div v-show="meta1">Parabéns! você alcançou a meta(v-show)</div>
  <div v-if="(likes >= 4) & (likes < 6)">
    Parabéns! você alcançou a meta {{ getLikes() }}(v-if)
  </div>
  <div v-else-if="likes >= 6">
    Parabéns! você alcançou a meta secreta troque o seu nome(v-elseif)
    <input type="text" v-model="nome" />
  </div>
  <div v-else>Continue Tentando({{ getLikes2 }})</div>
  <hr />
  <input type="number" v-model="valor" />
  <p>Valor combustivel:{{ valor }} com ICMS :{{ icms }}</p>
  <hr />
  <div>
    <h1>Frutas</h1>
    <ul>
      <li v-for="(fruta, i) in frutas" v-bind:key="i">
        {{ i }} -- {{ fruta }}
      </li>
    </ul>
  </div>
  <hr />
  <div>
    <h1>Carros</h1>
    <input
      type="text"
      placeholder="ID"
      :value="novocarro.id"
      @input="novocarro.id = $event.target.value"
    />
    <input type="text" v-model="novocarro.desc" />
    <button v-on:click="adicionarCarro">Adicionar</button>
    <div>{{ novocarro.id }} -- {{ novocarro.desc }}</div>
    <ul>
      <li v-for="carro in carros" :key="carro.id">
        <button @click="removerCarro(carro.id)">Remover</button>
        {{ carro.id }} -- {{ carro.desc }}
      </li>
    </ul>
  </div>
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
