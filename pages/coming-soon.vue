<template>
  <v-main>
    <!-- <v-img
      style="filter: blur(3px); -webkit-filter: blur(3px)"
      height="80vh"
      :src="require('assets/ripple-water.jpg')"
      transition="slide-x-transition"
      dark
    >
    </v-img> -->
    <!-- <div class="imageContainer">
      <h1
        style="line-height: 80vh"
        class="d-flex justify-center text-h2 font-weight-bold white--text"
      >
        Great things coming soon.
      </h1>
    </div> -->
    <!-- <v-container fluid class="pa-0 ma-0">
      <v-row no-gutters>
        <v-col cols="4">
          <v-img
            :height="'calc(100vh - ' + $vuetify.application.top + 'px)'"
            :src="require('assets/ocean-cover.jpg')"
            transition="slide-x-transition"
            dark
            gradient="to bottom, rgba(24,48,51,0.7), rgba(24,48,51,.7)"
          >
          </v-img>
        </v-col>
        <v-col cols="8" style="background-color: #183033">
          <div
            class="text-center d-flex align-center justify-center"
            style="height: 100%"
          >
            <div>
              <h1 class="white--text text-h3">Great things are coming soon.</h1>
              <br /><br />
              <v-btn nuxt to="/">home</v-btn>
            </div>
          </div>
        </v-col>
      </v-row>
    </v-container> -->
    <v-container fluid class="pa-0 ma-0">
      <v-row no-gutters>
        <v-col cols="12" style="background-color: #183033">
          <div
            class="text-center d-flex align-center justify-center"
            style="height: 100vh"
          >
            <div>
              <h1 class="white--text text-h3">Great things are coming soon.</h1>
              <br /><br />
              <v-btn nuxt to="/">home</v-btn>
            </div>
          </div>
        </v-col>
      </v-row>
    </v-container>
  </v-main>
</template>
<script>
export default {
  name: 'ComingSoonPage',
}
</script>
<style scoped>
.imageContainer {
  width: 100vw;
  height: 80vh;
  background-image: url('assets/ripple-water.jpg');
}
</style>
