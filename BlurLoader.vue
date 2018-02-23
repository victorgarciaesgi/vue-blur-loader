<template>
  <div ref='root' class='lazy-blur-background'>
    <div class='placeholder' v-if='!smallImgLoaded'>
      <slot></slot>
    </div>
    <img :src='smallImgSrc' class='imgPlaceHolder'>
    <img class='img-small lazy' :class='{loaded: smallImgLoaded}' :src='smallImgSrc' @load='handleSmallLoaded()'>
    <img :class='{loaded: bigImgLoaded}' :src='bigImgSrc' @load='handleBigLoaded()' class='lazy'>
  </div>
</template>

<script>
export default {
  name: 'BlurLoader',
  props: [
    'src', 'smallSrc'
  ],
  data() {
    return {
      smallImgSrc: null,
      bigImgSrc: null,
      smallImgLoaded: false,
      bigImgLoaded: false,
    }
  },
  methods: {
    handleSmallLoaded() {
      this.smallImgLoaded = true;
    },
    handleBigLoaded() {
      this.bigImgLoaded = true;
    }
  },
  mounted() {
    if(this.smallSrc) {
      this.smallImgSrc = this.smallSrc;
      this.bigImgSrc = this.src;
    } else {
      throw new Error('No small image source specified');
    }
  }
}
</script>

<style scoped>

.lazy-blur-background {
  position: relative;
  overflow: hidden;
}

img.lazy {
  position: absolute;
  display: block;
  top: 0;
  left: 0;
  opacity: 0;
  width: 100%;
  transition: opacity 1s linear;
}

img.lazy.loaded {
  opacity: 1;
}

img.imgPlaceHolder {
  position: relative;
  width: 100%;
  height: auto;
  opacity: 0;
}

.img-small {
  filter: blur(50px);
  transform: scale(1);
}

.placeholder {
  position: absolute;
  width: 100%;
  display: flex;
  justify-content: center;
  align-items: center;
  align-content: center;
  height: 100%;
  background-color: rgb(60,60,60);
}



</style>

