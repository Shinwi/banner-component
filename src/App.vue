<template>
  <div id="appContainer">
    <banner-component
      :mode="'sQuaRE'"
      :items="items"
    ></banner-component>
  </div>
</template>

<script>
import BannerComponent from './components/BannerComponent.vue';
export default {
  name: "App",
  components: {
    BannerComponent
  },
  data () {
    return {
      items: [
        {
          type: 'image',
          aspectRatio: 'square',
          src: 'https://picsum.photos/400',
          link: 'https://example.com/link1'
        },
        {
          type: 'cta',
          title: 'CTA Title',
          button: 'CTA Button',
          link: 'https://example.com/link2'
        },
        {
          type: 'image',
          aspectRatio: 'square',
          src: 'https://picsum.photos/400',
          link: 'https://example.com/link3'
        }
      ]
    }
  }
}
</script>
<style>
#appContainer {
  border: thin solid red;
  display: flex;
  align-items: center;
  justify-content: center;
  height: 100vh;
}
</style>
