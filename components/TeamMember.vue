<template>
  <v-col cols="6" sm="3">
    <v-card>
      <v-card-text>
        <div class="py-3"></div>
        <div class="mb-12" style="z-index: 1; position: relative">
          <v-row>
            <div class="mx-auto" style="width: 80%; aspect-ratio: 1/1">
              <v-avatar class="elevation-12 mx-auto" size="100%">
                <v-img :src="require(`assets/${innerimage}`)"></v-img>
              </v-avatar>
            </div>
          </v-row>

          <div style="z-index: 900; position: absolute; bottom: 2%; left: 60%">
            <v-btn
              class="mx-2"
              dark
              fab
              small
              color="primary"
              @click="overlay = !overlay"
            >
              <v-icon dark> mdi-arrow-right-bold </v-icon>
            </v-btn>
          </div>
        </div>
      </v-card-text>
      <v-overlay :value="overlay">
        <div v-click-outside="onClickOutside">
          <v-card
            width="100vw"
            style="max-width: 800px; max-height: 85vh"
            class="mx-auto overflow-auto"
          >
            <div style="position: relative">
              <v-btn
                dark
                fab
                small
                color="primary"
                @click="overlay = !overlay"
                style="position: absolute; right: 2px; top: 2px"
              >
                <v-icon dark> mdi-close </v-icon>
              </v-btn>
            </div>
            <v-container>
              <v-row class="justify-center">
                <v-col cols="8" sm="6" class="pa-6">
                  <v-img
                    :src="require(`assets/${innerimage}`)"
                    class="rounded-lg"
                  ></v-img>
                  <div class="text-center"></div>
                </v-col>
                <v-col
                  cols="12"
                  sm="6"
                  class="pa-12"
                  style="background: whitesmoke"
                >
                  <div class="black--text">
                    <h1 class="text-h4 font-weight-medium">{{ name }}</h1>
                    <h1 class="text-h6 font-weight-light">{{ title }}</h1>
                    <br />
                    <p>
                      {{ description }}
                    </p>
                    <v-btn
                      v-for="({ icon, link }, i) in socials"
                      :key="i"
                      class="black--text"
                      icon
                      link
                      target="_blank"
                      :href="link"
                    >
                      <v-icon large> {{ icon }} </v-icon>
                    </v-btn>
                    <!-- <v-btn
                      v-for="({ icon, link }, i) in socials"
                      :key="i"
                      class="white--text mr-3"
                      icon
                      link
                      :href="link"
                      target="_blank"
                    >
                      <v-icon large>
                        {{ icon }}
                      </v-icon>
                      <div class="px-10"></div>
                    </v-btn> -->
                  </div>
                </v-col>
              </v-row>
            </v-container>
            <!-- <v-card-title
            >Hello
            <v-spacer></v-spacer>
            <v-btn
              class="mx-2"
              dark
              fab
              small
              color="primary"
              @click="overlay = !overlay"
            >
              <v-icon dark> mdi-close </v-icon>
            </v-btn>
          </v-card-title>
          <v-card-text
            >Lorem ipsum dolor sit amet consectetur adipisicing elit. Recusandae
            ducimus corrupti veniam eaque esse, reiciendis eius! Dicta doloribus
            veniam fugit.</v-card-text
          > -->
          </v-card>
        </div>
      </v-overlay>
      <v-card-title class="justify-center"
        >{{ name }}
        <span><span>&nbsp;</span> <country-flag :country="countryFlag" /></span
      ></v-card-title>
      <v-card-subtitle class="text-center">
        {{ title }}
      </v-card-subtitle>
    </v-card>
  </v-col>
</template>

<script>
export default {
  props: {
    name: String,
    title: String,
    description: String,
    innerimage: String,
    socials: Array,
    countryFlag: String,
  },
  data: () => ({
    absolute: true,
    overlay: false,
  }),
  methods: {
    onClickOutside() {
      this.overlay = false
    },
  },
}
</script>
