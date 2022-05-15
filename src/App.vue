<template>
  <div id="app">
    <div class="titulos">GITCAT</div>

  <div class="area">
    <div>
      <div>
        <label for="title">Titulo de la foto</label>
      </div>
      <input
        v-model="title"
        name="title"
        value="title"
        class="input"
        type="text"
      />
    </div>
    <div>
      <label for="filter">Filtro de la foto</label>
    </div>
    <div>
      <select v-model="filter" class="input" id="" name="filter">
        <option v-for="(filter, index) in filters" :key="index" :value="filter">
          {{ filter }}
        </option>
      </select>
    </div>
    <div>
      <label for="filter">Color del texto</label>
    </div>
    <div>
      <select v-model="color" class="input" name="color" id="">
        <option v-for="(color, index) in colors" :key="index" :value="color">
          {{ color }}
        </option>
      </select>
    </div>
    <div>
      <label for="filter">Tamaño de foto</label>
    </div>
    <div><input v-model="size" class="input" type="text" /></div>
    <button @click="getUrl">OBTENER GATITO</button>

   </div>

    <div>
      <img
        @load="loaderActive = false"
        :src="url"
        v-show="url !== '' && !loaderActive"
      />
    </div>
    <Spinner :active="loaderActive" />
  </div>
</template>

<script>
import Spinner from "./components/Spinner.vue";

export default {
  name: "App",
  components: {
    Spinner,
  },

  data() {
    return {
      loaderActive: false,
      url: "",
      title: "",
      filters: ["blur", "mono", "sepia", "negative", "paint", "pixel"],
      colors: [
        "green",
        "black",
        "pink",
        "blue",
        "red",
        "yellow",
        "white",
        "purple",
      ],
      size: 0,
      imagen: "",

      filter: "blur",
      color: "green",
    };
  },
  methods: {
    getUrl() {
      this.loaderActive = true;
      this.url = `https://cataas.com/cat/gif/says/${this.title}?filter=${this.filter}&color=${this.color}&size=${this.size}&width=500&height=300`;
      console.log(this.url);
    },
  },
};
</script>

<style scoped>

.titulos {
  font-size: 50px;
  padding-top: 20px;
  font-weight: bold;
  color: #ff0000;
}

.area {
  background-color: #f08080;
  padding-top: 20px;
  padding-bottom: 20px;
}
#app {
  font-family: 'Trebuchet MS', 'Lucida Sans Unicode', 'Lucida Grande', 'Lucida Sans', Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  background-color: #add8e6;
}
.input {
  width: 300px;
  height: 50px;
  border-radius: 10px;
  margin: 10px 0;
}

button {
  background-color: rgb(0, 163, 212);
  padding-block: 20px;
  border-radius: 10px;
}
</style>
