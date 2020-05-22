<template>
  <div  class="x-ggb-container">
    <div id="ggb-element" v-resize="onResize"></div>
    <v-overlay :value="loading">
      <v-progress-circular indeterminate size="64"></v-progress-circular>
    </v-overlay>
  </div>
</template>

<script>
  import GGBApplet from '@/plugins/ggb'
  export default {
    name: 'GeoGebra',

    data: () => ({
      loading: true,
      ggbApp: null,
      sto: null
    }),

    mounted() {
      this.renderGGB()
    },
    methods: {
      renderGGB() {
        this.loading = true
        this.ggbApp = new GGBApplet({
          scaleContainerClass: "x-ggb-container",
          appName: "geometry",
          width: document.documentElement.clientWidth,
          height: document.documentElement.clientHeight,
          showToolBar: true,
          showAlgebraInput: true,
          showMenuBar: false,
          showFullscreenButton: false,
          showLogging: true,
          appletOnLoad: () => {
            setTimeout( () => {
              this.loading = false
            }, 500)
          }
        }, true);
        this.ggbApp.inject('ggb-element');

      },
      onResize () {
        if (this.ggbApp) {
          this.ggbApp.getAppletObject().setSize(document.documentElement.clientWidth,document.documentElement.clientHeight)
        }
      }
    }
  }
</script>
<style>
  .x-ggb-container{
    width: 100%;height: 100%;
  }
</style>
