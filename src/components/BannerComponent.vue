<template>
  <div>
    <b-container>
      <b-row class="text-center">
        <b-col sm="4" lg="4" md="4" v-for="(item, index) in items" :key="index">
          <a :href="item.link" target="_blank" v-if="item.type === 'image'" >
            <!-- TODO: show a loader spinner while the image is loading -->
            <img style='height: 100%; width: 100%; object-fit: contain' :src="item.src" @load="onImgLoad">
          </a>
          <div v-else-if="item.type === 'cta'" id="cta">
            <b-row style="margin-top: 3em;">
              <h3><strong>{{ item.title }}</strong></h3>
            </b-row>
            <b-row style="margin-top: 2em;">
              <a :href="item.link" target="_blank" class="cta-button"><strong>{{ item.button }}</strong></a>
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
  data () {
    return {
      isImageLoaded: false,
    }
  },
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
  },
  /*
    Since the background color of the cta div is random:
    - we create an array of colors
    - select a random color from it
    - assign it to cta div when the page is rendered.
    I only used 3 colors here (the one used in the design documents, but we can add more if we wish to.)
  */
  mounted () {
    var colors = ['lightblue', 'lightgreen', 'lightgray'];
    var random_color = colors[Math.floor(Math.random() * colors.length)];
    document.getElementById('cta').style.background = random_color;
  },
  methods: {
    onImgLoad () {
      this.isImageLoaded = true
    }
  }
}
</script>
<style>
#cta {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  height: 100%; /* so that the div can fill the entire col-4 container*/
}
/* Overriding the paddings in col-4 original styling to remove spaces between divs in the component*/
.col-lg-4, .col-md-4, .col-sm-4 {
  padding-right: 0 !important;
  padding-left: 0 !important;
}
.cta-button {
  border: thin solid black;
  padding: 10px 30px;
}
a {
  text-decoration: none;
  color: inherit;
}
a:hover {
  text-decoration: none;
}
</style>