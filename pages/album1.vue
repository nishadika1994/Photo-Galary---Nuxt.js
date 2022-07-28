<template>
  <div class="main">
    <div class="heading">
      <h2>ALBUM {{ albumNumber }}</h2>
    </div>
    <div class="albums" v-for="(item, index) in images" :key="index">
      <div v-if="item.albumId == alubumNum" class="img-container">
        <a :href="item.url" target="_blank"><img :src="item.url" /></a>
        <h1>Album ID : {{ item.albumId }} Image ID : {{ item.id }}</h1>
      </div>
    </div>
  </div>
</template>
<script>
export default {
  asyncData({ params, error }) {
    return {
        images: params.userId,
        alubumNum: params.albumID,
    }
  },
  data() {
    return {
    };
  },
  computed: {
    albumNumber() {
      return this.alubumNum;
    },
  },
  created() {
    // this.images = this.$route.params.userId;
    // this.alubumNum = this.$route.params.albumID;
    // console.log(this.$route.params.userId);
  },
};
</script>
<style scoped>
h2 {
  position: relative;
  font: 3em sans-serif;
  font-size: 400%;
}
h1 {
  position: relative;
  font: 3em sans-serif;
  font-size: 150%;
  padding: 20px;
  font: 20px Arial, sans-serif;
}
.img-container {
  width: 25%;
  float: left;
}
img {
  max-width: 100%;
}
.main {
  margin: 100px;
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
</style>
