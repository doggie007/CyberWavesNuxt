<template>
  <v-app>
    <v-navigation-drawer
      v-model="drawer"
      absolute
      temporary
      right
      style="position: fixed; top: 0; right: 0; overflow-y: scroll"
    >
      <v-list nav dense>
        <v-list-item-group class="mt-5">
          <v-list-item
            v-for="({ icon, link, name }, i) in links"
            :key="i"
            :to="link"
          >
            <v-list-item-icon>
              <v-icon>{{ icon }}</v-icon>
            </v-list-item-icon>
            <v-list-item-title class="text-button font-weight-bold">{{
              name
            }}</v-list-item-title>
          </v-list-item>
        </v-list-item-group>
      </v-list>
    </v-navigation-drawer>

    <v-app-bar app color="white" height="80%">
      <NuxtLink to="/">
        <v-avatar class="mr-3" color="grey lighten-5" size="70">
          <v-img
            contain
            max-height="70%"
            src="https://cdn.vuetifyjs.com/images/logos/vuetify-logo-dark.png"
          ></v-img>
        </v-avatar>
      </NuxtLink>
      <NuxtLink style="text-decoration: none; color: inherit" to="/">
        <v-toolbar-title class="font-weight-black">
          CYBERWAVES
        </v-toolbar-title>
      </NuxtLink>
      <v-toolbar-items class="ml-12 hidden-sm-and-down">
        <v-btn v-for="({ link, name }, i) in links" :key="i" text :to="link">{{
          name
        }}</v-btn>
      </v-toolbar-items>
      <v-spacer></v-spacer>

      <!-- Hamburger menu -->
      <v-app-bar-nav-icon
        class="hidden-md-and-up"
        @click="drawer = true"
      ></v-app-bar-nav-icon>
      <!-- <v-tabs align-with-title class="hidden-sm-and-down">
				<v-tab v-for="link in links" :key="link" text>{{ link }}</v-tab>
			</v-tabs> -->
    </v-app-bar>

    <!-- Views rendered  -->
    <!-- <v-scroll-x-transition mode="in" hide-on-leave="true"> -->
    <Nuxt></Nuxt>
    <!-- </v-scroll-x-transition> -->

    <v-footer dark padless class="justify-center">
      <v-card
        flat
        tile
        class="font-weight-normal grey--text text--lighten-1 text-center"
        width="100%"
      >
        <v-card-text>
          <v-container>
            <v-row class="text-left">
              <v-col>
                <p class="text-h5">CyberWaves</p>
              </v-col>
            </v-row>
            <v-row class="text-left text-subtitle-2 text-sm-subtitle-1">
              <v-col>
                <p>Organisation</p>
                <NuxtLink to="/about">About Us</NuxtLink>
                <br />
                <NuxtLink
                  :to="{ path: '/about', hash: 'five-principles-intro' }"
                  >Our Belief</NuxtLink
                >
                <br />
                <NuxtLink :to="{ path: '/about', hash: 'our-team' }"
                  >Our Team</NuxtLink
                >
              </v-col>
              <v-col>
                <p>Products & Services</p>
                <NuxtLink to="/coming-soon">Splastic</NuxtLink>
                <br />
                <NuxtLink to="/coming-soon">SeaVision</NuxtLink>
              </v-col>
              <v-col>
                <p>Education</p>
                <NuxtLink to="/coming-soon">Technologies</NuxtLink>
                <br />
              </v-col>
            </v-row>
            <v-divider class="my-12"></v-divider>

            <v-row class="text-left">
              <v-col>
                <v-btn
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
                  <!-- <div class="px-10"></div> -->
                </v-btn>
              </v-col>
            </v-row>
            <v-row class="text-left">
              <v-col>
                &copy;{{ new Date().getFullYear() }} — Made with 💙 by
                <strong>The CyberWaves Team</strong>
              </v-col>
            </v-row>
          </v-container>
        </v-card-text>
      </v-card>

      <!-- <v-card
        flat
        tile
        class="font-weight-light grey--text text--lighten-1 text-center"
        width="100%"
      >
        <v-card-text>
          <v-btn
            v-for="({ icon, link }, i) in socials"
            :key="i"
            class="mx-4 white--text"
            icon
            link
            :href="link"
            target="_blank"
          >
            <v-icon x-large>
              {{ icon }}
            </v-icon>
          </v-btn>
        </v-card-text>
        <v-list>
          <v-list-item-group>
            <v-list-item
              v-for="({ link, name }, i) in links"
              :key="i"
              :to="link"
            >
              <v-list-item-title class="text-button font-weight-bold">{{
                name
              }}</v-list-item-title>
            </v-list-item>
          </v-list-item-group>
        </v-list>

        <v-card-text class="white--text text--lighten-1">
          Lorem ipsum dolor sit amet consectetur, adipisicing elit. Distinctio,
          assumenda a. Porro exercitationem sit voluptatibus magnam et,
          molestiae officia aspernatur.
        </v-card-text>

        <v-divider></v-divider> -->
      <!-- <div>&copy; {{ new Date().getFullYear() }}</div> -->

      <!-- <v-card-text class="font-weight-light white--text text-center">
          &copy;{{ new Date().getFullYear() }} — Made with 💙 by
          <strong>James Tcheng</strong>
        </v-card-text>
      </v-card> -->
    </v-footer>
  </v-app>
</template>

<script>
export default {
  name: 'App',
  data() {
    return {
      drawer: false,
      links: [
        { icon: 'mdi-home-outline', link: '/', name: 'Home' },
        { icon: 'mdi-information-outline', link: '/about', name: 'About' },
        { icon: 'mdi-school-outline', link: '/learn', name: 'Learn' },
      ],
      socials: [
        {
          icon: 'mdi-instagram',
          link: 'https://www.instagram.com/cyberwavesorg',
        },
        {
          icon: 'mdi-github',
          link: 'https://github.com/doggie007/CyberWavesNuxt',
        },
      ],
    }
  },
}
</script>

<style scoped>
a:link {
  text-decoration: none;
}
a:hover {
  opacity: 0.7;
}
</style>
e
