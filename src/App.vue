<template>
  <div class="body vh-100" id="app">
    <LoadingPage v-once />

    <h1 class="title" v-show="!tituloRecibido">DeliMar</h1>
    <div class="wrapper" v-show="!tituloRecibido">
      <CardS
        @escuchar="RecibirTitulo"
        v-for="(producto, index) in tipos"
        :key="index"
        :idC="index + producto.titulo"
        :titulo="producto.titulo"
        :descipcion="producto.descipcion"
        :img="producto.img"
        :color="producto.color"
        :precio="producto.precio"
      />
    </div>
    <ProductO
      v-show="tituloRecibido"
      :titulo="tituloRecibido"
      :descipcion="descipcionRecibida"
      :img="imagenRecibida"
      :precio="precioRecibido"
    />
    <button v-show="tituloRecibido" v-on:click="volver">
      <b-row align-h="end" class="volver">
        <b-col cols="5">
          <svg
            xmlns="http://www.w3.org/2000/svg"
            fill="currentColor"
            class="bi bi-arrow-left-circle-fill"
            viewBox="0 0 16 16"
          >
            <path
              d="M8 0a8 8 0 1 0 0 16A8 8 0 0 0 8 0zm3.5 7.5a.5.5 0 0 1 0 1H5.707l2.147 2.146a.5.5 0 0 1-.708.708l-3-3a.5.5 0 0 1 0-.708l3-3a.5.5 0 1 1 .708.708L5.707 7.5H11.5z"
            /></svg
        ></b-col>
      </b-row>
    </button>
  </div>
</template>

<script>
import LoadingPage from "./components/LoadingPage.vue";
import CardS from "./components/Card.vue";
import ProductO from "./components/Producto.vue";

export default {
  name: "App",
  components: {
    CardS,
    LoadingPage,
    ProductO,
  },
  data() {
    return {
      tituloRecibido: null,
      descipcionRecibida: null,
      imagenRecibida: null,
      precioRecibido: null,
      tipos: [
        {
          titulo: "Sushi",
          descipcion:
            "Comida japonesa elaborada con pescado crudo y gran variedad de ingredientes y condimentos.",
          img: require("@/img/min/sushi.jpg"),
          enlace: "",
          color: "rgb(42, 171, 29)",
          precio: "$80.000",
        },
        {
          titulo: "Mariscos",
          descipcion:
            "Comida japonesa elaborada con pescado crudo y gran variedad de ingredientes y condimentos.",
          img: require("@/img/min/mariscos.jpg"),
          enlace: "",
          color: "rgb(255, 187, 0)",
          precio: "$60.000",
        },
        {
          titulo: "Ceviche",
          descipcion:
            "Comida japonesa elaborada con pescado crudo y gran variedad de ingredientes y condimentos.",
          img: require("./img/min/ceviche.jpg"),
          enlace: "#seccion",
          color: "rgb(255, 251, 0)",
          precio: "$75.000",
        },
      ],
      arrayFiltrado: [],
    };
  },
  methods: {
    RecibirTitulo(titulo, descipcion, imagen, precio) {
      this.tituloRecibido = titulo;
      this.descipcionRecibida = descipcion;
      this.imagenRecibida = imagen;
      this.precioRecibido = precio;
    },
    volver() {
      this.tituloRecibido = false;
    },
  },
};
</script>

<style>
.v-enter-active,
.v-leave-active {
  transition: opacity 1.5s ease;
}

.v-enter-from,
.v-leave-to {
  opacity: 0;
}
@font-face {
  font-family: Gigi Script;
  src: url(./fonts/GIGI.TTF);
}
:root {
  --white: rgba(255, 255, 255, 1);
  --second: rgb(48, 71, 121);
  --grend: rgb(202, 214, 238);
  --font-family-gigi-regular: "Gigi Script";
  --background: url(./img/min/background1.png);
}
* {
  margin: 0;
  padding: 0;
}
#app {
  background-image: url(./img/min/background1.png);
  background-position: 65%;
  background-attachment: fixed;
  background-size: cover;
  background-repeat: no-repeat;
  /* position: fixed; */
  font-family: var(--font-family-gigi-regular);
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: var(--white);
  transition: 0.8s ease all;
}
.volver {
  width: 50%;
  position: fixed;
  right: 7vw;
  bottom: 6vh;
  z-index: 999;
}
.volver svg {
  color: #fff4b6;
}
.title {
  padding-top: 5%;
  font-size: 20vw;
  -webkit-text-stroke: 0.1px var(--second);
}

.wrapper {
  display: flex;
  overflow-x: scroll;
  scroll-snap-type: x mandatory;
}
.wrapper::-webkit-scrollbar {
  background: transparent;
}
.cards {
  scroll-snap-align: center;
}
.slide-up-enter-active,
.slide-up-leave-active {
  transition: all 0.25s ease-out;
}

.slide-up-enter-from {
  opacity: 0;
  transform: translateY(30px);
}
.card {
  margin: auto;
  height: 500px;
  width: 200px;
  background: yellowgreen !important;
}
.slide-up-leave-to {
  opacity: 0;
  transform: translateY(-30px);
}
</style>
