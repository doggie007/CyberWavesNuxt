<template>
  <v-col cols="12" md="10">
    <v-row align="center" justify="center" no-gutters>
      <v-col cols="6" sm="8">
        <v-card flat tile :height="450" color="grey lighten-1" dark>
          <v-img
            :src="require(`@/assets/${value.hero}`)"
            height="100%"
            gradient="rgba(0, 0, 0, .35), rgba(0, 0, 0, .35)"
          >
            <v-row v-if="!value.prominent" class="fill-height text-right ma-0">
              <v-col cols="12">
                <v-chip
                  label
                  class="mx-0 mb-2 text-uppercase"
                  color="grey darken-3"
                  text-color="white"
                >
                  {{ value.category }}
                </v-chip>

                <h3 class="text-h5 font-weight-bold mb-2">
                  {{ value.title }}
                </h3>
              </v-col>

              <v-col align-self="end">
                <v-chip
                  class="text-uppercase ma-0"
                  color="primary"
                  label
                  small
                  nuxt
                  :to="value.link"
                >
                  Read More
                </v-chip>
              </v-col>
            </v-row>
          </v-img>
        </v-card>
      </v-col>

      <v-col cols="6" sm="4">
        <v-card
          tile
          flat
          :height="450"
          color="rgb(245,245,245)"
          outlined
          class="overflow-auto"
        >
          <v-row class="text-right ma-0">
            <v-col cols="12">
              <div class="subtitle-2">
                Author: {{ value.author }}<br />
                Published: {{ value.date }}
              </div>
              <br />
              <div class="body-1 text-justify">
                {{ value.description }}
              </div>
            </v-col>
          </v-row>
        </v-card>
      </v-col>
    </v-row>
  </v-col>
</template>

<script>
export default {
  name: 'FeedCard',

  props: {
    size: {
      type: Number,
      required: true,
    },
    value: {
      type: Object,
      default: () => ({}),
    },
  },
}
</script>

<style>
.v-image__image {
  transition: 0.3s linear;
}
</style>
