<template>
  <div class="main">
    <div class="heading">
      <h1>Photo Galary</h1>
    </div>
    <div class="albums">
      <el-button class="btn1"
        ><nuxt-link
          :to="{ name: 'album1', params: { userId: posts, albumID: 1 } }"
          >Alubum 01</nuxt-link
        ></el-button
      >
      <el-button class="btn2"
        ><nuxt-link
          :to="{ name: 'album1', params: { userId: posts, albumID: 2 } }"
          >Alubum 02</nuxt-link
        ></el-button
      >
      <el-button class="btn3"
        ><nuxt-link
          :to="{ name: 'album1', params: { userId: posts, albumID: 3 } }"
          >Alubum 03</nuxt-link
        ></el-button
      ><br />
      <el-button class="btn4"
        ><nuxt-link
          :to="{ name: 'album1', params: { userId: posts, albumID: 4 } }"
          >Alubum 04</nuxt-link
        ></el-button
      >
      <el-button class="btn5"
        ><nuxt-link
          :to="{ name: 'album1', params: { userId: posts, albumID: 5 } }"
          >Alubum 05</nuxt-link
        ></el-button
      >
      <el-button class="btn6"
        ><nuxt-link
          :to="{ name: 'album1', params: { userId: posts, albumID: 6 } }"
          >Alubum 06</nuxt-link
        ></el-button
      >
    </div>
  </div>
</template>

<script>
import axios from "axios";
var images;
export default {
  
  data() {
    return {
      posts: null,
    };
  },
  created() {
    this.init()
  },
  methods: {
    async init() {
      await axios
        .get(`https://jsonplaceholder.typicode.com/photos`)
        .then((response) => {
          this.posts = response.data;
          images = response["data"];
          console.log(images);
          debugger;
        })
        .catch((e) => {
          console.log("Error Please check the connection");
        });
    },
  },
};
</script>
<style scoped>
h1 {
  position: relative;
  font: 3em sans-serif;
  font-size: 400%;
}
.main {
  margin: 100px;
}
.albums {
  margin-left: 200px;
}
.heading {
  text-align: center;
}
.link {
  display: flex;
  align-items: center;

  cursor: pointer;
  position: relative;
  font-weight: 600;
  user-select: none;
  font: bold;
  font-size: 300%;

  margin: 0.1em 0;
  padding: 0.4em;
  border-radius: 0.25em;
  height: 1.5em;

  color: rgb(85, 85, 87);
  text-decoration: none;
}

.link:hover {
  background-color: var(--sidebar-item-hover);
}

.link.active {
  background-color: var(--sidebar-item-active);
}
::v-deep .el-button {
  width: 300px;
  height: 300px;
  margin: 20px;
  font: bold;
}
.btn1 {
  background-color: blue;
  font: bold;
  font-size: 200%;
}
.btn2 {
  background-color: orangered;
  font: bold;
  font-size: 200%;
}
.btn3 {
  background-color: yellow;
  font: bold;
  font-size: 200%;
}
.btn4 {
  background-color: green;
  font: bold;
  font-size: 200%;
}
.btn5 {
  background-color: darkblue;
  font: bold;
  font-size: 200%;
}
.btn6 {
  background-color: red;
  font: bold;
  font-size: 200%;
}
</style>
