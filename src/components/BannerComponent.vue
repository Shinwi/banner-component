<template>
  <div>
    <h2>hello im component</h2>
    <div>
      <h2>mode : {{ mode }}</h2>
    </div>
    <div>
      <h2>carous : {{ carouselOnMobil }}</h2>
    </div>
    <div>
      <h2>items : {{ items }}</h2>
    </div>
 </div>
</template>

<script>
export default {
  name: 'BannerComponent',
  props: {
    mode: {
      type: String,
      required: true,
      validator: function (value) {
        return ['square', 'rectangle'].includes(value.toLowerCase())
      }
    },
    items: {
      type: Array,
      required: true
    },
    carouselOnMobil: {
      type: Boolean,
      default: false
    }
  }
}
</script>
