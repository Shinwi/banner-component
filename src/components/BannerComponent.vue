<template>
  <div>
    <b-container >
      <b-row class="text-center">
        <b-col cols="4" v-for="(item, index) in items" :key="index">
          <img style='height: 100%; width: 100%; object-fit: contain' v-if="item.type === 'image'" :src="item.src">
          <div v-else-if="item.type === 'cta'" class="cta">
            <b-row>
              <strong>{{ item.title }}</strong>
            </b-row>
            <b-row>
              <button>{{ item.button }}</button>
            </b-row>
          </div>
        </b-col>
      </b-row>
    </b-container>
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
<style>
.cta {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
}
</style>