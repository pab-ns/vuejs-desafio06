<template>
  <div>
    <header>
      <h1>Random GIF Cat</h1>
    </header>

    <form @submit.prevent="generarNuevoGatitoUrl()">
      <div class="formulario">
        <label for="titulo">Título: </label>
        <input
          type="text"
          required
          name="titulo"
          minlength="3"
          maxlength="20"
          v-model="formulario.titulo"
        />

        <br />
        <br />

        <label for="filtro">Filtro: </label>
        <select required name="filtro" v-model="formulario.filtro">
          <option value="blur">Blur</option>
          <option value="mono">Mono</option>
          <option value="sepia">Sepia</option>
          <option value="negative">Negative</option>
          <option value="paint">Paint</option>
          <option value="pixel">Pixel</option>
        </select>

        <br />
        <br />

        <label for="color">Color: </label>
        <select required name="color" v-model="formulario.color">
          <option value="blue">Azul</option>
          <option value="red">Red</option>
          <option value="yellow">Amarillo</option>
          <option value="orange">Naranja</option>
          <option value="purple">Morado</option>
        </select>
        <div
          style="width: 15px; height: 15px; border-radius: 50%; display: inline-block"
          :style="{ 'background-color': formulario.color }"
        ></div>

        <br />
        <br />

        <label for="tamano">Tamaño: </label>
        <input
          type="number"
          required
          name="tamano"
          step="100"
          min="100"
          max="900"
          v-model.number="formulario.tamano"
        />
      </div>

      <div class="catShow">
        <br />
        <br />
        <button type="submit">Obtener gato</button>
      </div>
    </form>

    <div class="catShow">
      <img alt="" :src="gatoUrl" />
    </div>

    <!-- <pre>formulario: {{ formulario }}</pre> -->
  </div>
</template>

<script>
export default {
  name: "App",
  data: () => ({
    gatoUrl: "",
    formulario: {
      titulo: null,
      filtro: null,
      color: null,
      tamano: null,
    },
  }),
  methods: {
    generarNuevoGatitoUrl() {
      console.log(this.formulario);
      this.gatoUrl = `https://cataas.com/cat/gif/says/${this.formulario.titulo}?filter=${this.formulario.filtro}&color=${this.formulario.color}&width${this.formulario.tamano}`;
    },
  },
};
</script>

<style>
body {
  font-family: sans-serif;
}

header {
  padding: 2rem 0;
  background-color: aquamarine;
  text-align: center;
}

.formulario {
  padding: 2rem 0;
  background-color: #eb817d;
  text-align: center;
}

.catShow {
  background-color: aquamarine;
  text-align: center;
}

.catShow img {
  margin-top: 1rem;
  margin-bottom: 3rem;
}
</style>
