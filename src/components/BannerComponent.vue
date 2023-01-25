<template>
  <div>
    <b-container>
      <b-row v-if="mode.toLowerCase() === 'square'" class="text-center">
        <b-col sm="4" lg="4" md="4" v-for="(item, index) in items" :key="index">
          <a :href="item.link" target="_blank" v-if="item.type === 'image'" >
            <img class="fit-image-in-container" :src="item.src" @load="onImgLoad">
          </a>
          <div v-else-if="item.type === 'cta'" id="align-items-cta" style="height:100%;">
            <h3><strong>{{ item.title }}</strong></h3>
            <a :href="item.link" target="_blank" class="cta-button"><strong>{{ item.button }}</strong></a>
          </div>
        </b-col>
      </b-row>
      <b-row v-else-if="mode.toLowerCase() === 'rectangle'" class="text-center">
        <b-col lg="8">
          <a :href="getRectangleModeImage.link" target="_blank">
            <img :src="getRectangleModeImage.src" class="fit-image-in-container">
          </a>
        </b-col>
        <b-col lg="4" id="align-items-cta" :style="'background:' + (isMobile ? 'white;' : 'lightblue;')">
          <h3><strong>{{ getRectangleModeCTA.title }}</strong></h3>
          <a :href="getRectangleModeCTA.link" target="_blank" class="cta-button"><strong>{{ getRectangleModeCTA.button }}</strong></a>
        </b-col> 
      </b-row>
      <b-row v-else>
        <h2 style="color:red">Invalid props</h2>
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
      windowWidth: window.innerWidth
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
  mounted () {
    window.addEventListener('resize', () => {
      this.windowWidth = window.innerWidth
    })

    /*
      Since the background color of the cta div in desktop mode is random:
      - we create an array of colors
      - select a random color from it
      - assign it to cta div when the page is rendered.
      I only used 3 colors here (the one used in the design documents, but we can add more if we wish to.)
      If we are in phone mode, background is set to white
    */
    if (!this.isMobile) {
      var colors = ['lightblue', 'lightgreen', 'lightgray']
      var random_color = colors[Math.floor(Math.random() * colors.length)]
      document.getElementById('align-items-cta').style.background = random_color
    }
  },
  computed: {
    isMobile () {
      return this.windowWidth <= 760
    },
    getRectangleModeImage () {
      return this.isMobile ? this.items.filter(i => i.type === 'image' && i.aspectRatio !== 'rectangle')[0] : this.items.filter(i => i.type === 'image' && i.aspectRatio !== 'square')[0]
    },
    getRectangleModeCTA () {
      return this.items.filter(i => i.type === 'cta')[0]
    }
  },
  methods: {
    onImgLoad () {
      this.isImageLoaded = true
    }
  }
}
</script>
<style>
/* Overriding the paddings in col-4 original styling to remove spaces between divs in the component*/
.col-lg-4, .col-lg-8, .col-md-4, .col-sm-4 {
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
.fit-image-in-container {
  height: 100%; 
  width: 100%; 
  object-fit: contain
}
#align-items-cta {
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
}
</style>