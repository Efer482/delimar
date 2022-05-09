<template>
  <div class="producto vh-100">
    <b-container fluid>
      <b-row align-h="center">
        <b-col class="contenedor_imagen" cols="12">
          <img class="imagen" :src="img" alt="" />
          <b-row class="informacion">
            <b-col cols="12"
              ><h1>{{ titulo }}</h1></b-col
            >
            <b-col cols="12">
              <p>
                {{ descipcion }}
              </p>
            </b-col>
            <b-col>
              <br />
              <h3>
                {{ precio }}
              </h3>
            </b-col>
          </b-row>
        </b-col>
      </b-row>
    </b-container>
  </div>
</template>

<script>
export default {
  name: "ProductO",
  props: {
    titulo: {
      type: String,
      default: "Click",
    },
    descipcion: {
      type: String,
      default: "Click",
    },
    img: {
      type: String,
      default: "Click",
    },
    precio: {
      type: String,
      default: "Click",
    },
  },
};
</script>
<style scoped>
h1 {
  font-size: 11vw;
}
p {
  font-family: Georgia, "Times New Roman", Times, serif;
  font-size: 5vw !important;
}
h3 {
  font-size: 7vw;
  color: var(--grend);
}
.contenedor_imagen {
  overflow: hidden;
}
.imagen {
  width: 120vw;
  height: 120vw;
  transform: translate(-0%, -50%);
  clip-path: circle(38% at 50% 50%);
  -webkit-animation: ampliar 2s 0.6s forwards;
}
@keyframes ampliar {
  0% {
    transform: translate(-10%, -50%);

    clip-path: circle(38% at 50% 00%);
  }
  100% {
    transform: translate(-10%, -00%);

    clip-path: circle(38% at 50% 50%);
  }
}
.informacion {
  /* transform: translateY(-250%); */
}
.producto {
  background: rgba(0, 0, 0, 0.404);
}
</style>
