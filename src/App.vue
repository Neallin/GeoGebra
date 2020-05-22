<template>
  <v-app>
   <!-- <v-app-bar
      app
      color="primary"
      dark
    >
      <div class="d-flex align-center">
      </div>
      <v-spacer></v-spacer>
    </v-app-bar>-->

    <v-content>
      <GeoGebra/>
    </v-content>
  </v-app>
</template>

<script>
import GeoGebra from './components/GeoGebra';

export default {
  name: 'App',

  components: {
    GeoGebra,
  },

  data: () => ({
    //
  }),
};
</script>
<style>
    html,body{
        width: 100%;height: 100%;
        position: relative;
        overflow: hidden;
    }
</style>
