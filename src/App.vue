<template>
  <div id="appContainer">
    <banner-component
      :mode="'square'"
      :items="items"
    ></banner-component>
    <!-- 
    <banner-component
      :mode="'square'"
      :items="items2"
    ></banner-component> -->
    <!-- <banner-component
      :mode="'rectangle'"
      :items="rectangleItems"
    ></banner-component> -->
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
      ],
      items2: [
        {
          type: 'cta',
          title: 'CTA Title',
          button: 'CTA Button',
          link: 'https://example.com/link1'
        },
        {
          type: 'image',
          aspectRatio: 'square',
          src: 'https://picsum.photos/400',
          link: 'https://example.com/link2'
        },
        {
          type: 'image',
          aspectRatio: 'square',
          src: 'https://picsum.photos/400',
          link: 'https://example.com/link3'
        },
        {
          type: 'image',
          aspectRatio: 'square',
          src: 'https://picsum.photos/400',
          link: 'https://example.com/link3'
        },
        {
          type: 'image',
          aspectRatio: 'square',
          src: 'https://picsum.photos/400',
          link: 'https://example.com/link3'
        },
        {
          type: 'image',
          aspectRatio: 'square',
          src: 'https://picsum.photos/400',
          link: 'https://example.com/link3'
        }
      ],
      rectangleItems: [
        {
          type: 'image',
          aspectRatio: 'rectangle',
          src: 'https://picsum.photos/1200/400',
          link: 'https://example.com/link1'
        },
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
          link: 'https://example.com/link1'
        }
      ]
    }
  }
}
</script>
<style>
#appContainer {
  display: flex;
  align-items: center;
  justify-content: center;
  height: 100vh;
}
</style>
