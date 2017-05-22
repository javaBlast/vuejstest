<template>
  <div id="app">
    <transition name="slide-fade" class="fadeView">
      <div v-if="show">
        <image-view :imgArr="imgArr" :showImageView="true" :imageIndex="imageIndex" v-on:hideImage="hideImageView"></image-view>
      </div>
    </transition>
    <h1 @click="showImgView">显示隐藏</h1>
    <img v-for="(item, index) in imgArr" :src="item" @click="selectImg(index)">
  </div>
</template>

<script>
import imageView from 'vue-imageview'


export default {
  name: 'app',
  components: {
    'image-view': imageView
  },
  data() {
    return {
      imgArr: ['/src/assets/Yellow Daisies.jpg'],
      show: false,
      imageIndex: 2
    }
  },
  methods: {
    showImgView() {
      this.show = true
    },
    hideImageView() {
      this.show = false
    },
    selectImg(index) {
      this.show = true
      this.imageIndex = index
    }
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

h1,
h2 {
  font-weight: normal;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  display: inline-block;
  margin: 0 10px;
}

a {
  color: #42b983;
}

.slide-fade-enter-active {
  transition: opacity .5s ease;
}

.slide-fade-leave-active {
  transition: opacity .5s ease;
}

.slide-fade-enter,
.slide-fade-leave-active {
  opacity: 0;
}

h1,
h2 {
  margin: 0;
  padding: 0;
}

img {
  display: block;
  margin: 10px auto;
  max-width: 400px;
}
</style>
