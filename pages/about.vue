<template>
  <v-main>
    <!-- Intro -->
    <section id="our-vision">
      <v-container
        fluid
        class="pa-6"
        style="
          background-image: linear-gradient(to bottom left, #dbfcff, #fddcc356);
        "
        :style="{ height: 'calc(100vh - ' + $vuetify.application.top + 'px)' }"
      >
        <!-- <v-responsive
				class="pa-10"
				style="
					background-image: linear-gradient(to bottom left, #dbfcff, #fddcc356);
				"
				:max-height="{
					height: 'calc(100vh - ' + $vuetify.application.top + 'px)',
				}"
				min-width="100vw"
			> -->
        <v-layout fill-height>
          <v-flex align-self-center class="d-flex justify-center">
            <v-img
              :style="{
                height: 'calc(100vh - ' + $vuetify.application.top + 'px)',
              }"
              class="rounded"
              min-width="260"
              width="25vw"
              max-width="500"
              transition="slide-x-transition"
              :src="require('assets/rocky-beach.jpg')"
              gradient="to bottom, rgba(0,0,0,0.2), rgba(50,0,50,.3)"
            ></v-img>
          </v-flex>
          <v-flex
            align-self-center
            class="d-flex justify-center"
            style="margin-left: -55%"
          >
            <v-card
              outlined
              class="rounded-tl-xl rounded-br-xl overflow-auto"
              width="100%"
              elevation="24"
              min-width="230"
              max-width="800"
              :max-height="'calc(100vh - ' + $vuetify.application.top + 'px)'"
              color="#274156"
              dark
            >
              <v-card-title
                class="text-h4 text-sm-h3 font-weight-bold mb-3 text-uppercase"
                >Our Vision</v-card-title
              >
              <v-card-subtitle>
                <v-responsive width="56">
                  <v-divider
                    class="mb-1"
                    style="background: whitesmoke"
                  ></v-divider>
                  <v-divider style="background: white"></v-divider>
                </v-responsive>
              </v-card-subtitle>
              <p
                class="text-subtitle-2 text-sm-body-1 text-lg-h6 font-weight-light pa-5 text-justify"
              >
                We envision a better world where technology helps us to bridge
                the gap between our desire for a healthy planet and achievable +
                actionable solutions. We hope that through education and
                demonstrating the power of current technology, we can help other
                organisations and empower communities to be fearless at solving
                the ocean pollution problem themselves.
              </p>
              <v-btn
                class="ma-3 align-self-center"
                fab
                outlined
                @click="$vuetify.goTo('#sdgs')"
              >
                <v-icon>mdi-chevron-double-down</v-icon>
              </v-btn>
            </v-card>
          </v-flex>
        </v-layout>
      </v-container>
      <!-- </v-responsive> -->
    </section>

    <!-- Sdgs -->
    <section id="sdgs">
      <div class="py-5"></div>
      <v-container fluid>
        <v-row align-content="center" justify="center">
          <v-col cols="12">
            <v-flex>
              <p class="text-h5 font-weight-bold text-center text-md-h4">
                “Plastic pollution free world is not a choice but a commitment
                to life – <br />
                a commitment to the next generation.” - Amit Ray
              </p>
            </v-flex>
          </v-col>
        </v-row>
        <v-row justify="center">
          <v-col cols="12" style="max-width: 80vw">
            <p class="text-body-2 text-md-body-1 font-weight-bold text-left">
              We all have to play a part in the fight to save our oceans. Ocean
              plastic pollution destroys ecosystems below and above water,
              affects the health and livelihoods of the most vulnerable
              communities, and jeopardises its key role as a carbon sink which
              directly tackles climate change.
            </p>
          </v-col>
        </v-row>
        <v-row justify="center" class="pt-1">
          <v-col cols="2">
            <v-img
              min-width="50"
              max-width="150"
              transition="slide-x-transition"
              :src="require('assets/sdg-14.png')"
            ></v-img>
          </v-col>

          <v-col cols="2">
            <v-img
              min-width="50"
              max-width="150"
              transition="slide-x-transition"
              :src="require('assets/sdg-15.png')"
            ></v-img>
          </v-col>
          <v-col cols="2">
            <v-img
              min-width="50"
              max-width="150"
              transition="slide-x-transition"
              :src="require('assets/sdg-12.png')"
            ></v-img>
          </v-col>
          <v-col cols="2">
            <v-img
              min-width="50"
              max-width="150"
              transition="slide-x-transition"
              :src="require('assets/sdg-13.jpg')"
            ></v-img>
          </v-col>
          <v-col cols="2">
            <v-img
              min-width="50"
              max-width="150"
              transition="slide-x-transition"
              :src="require('assets/sdg-10.png')"
            ></v-img>
          </v-col>
        </v-row>
      </v-container>
    </section>
    <div class="py-12">
      <v-divider></v-divider>
    </div>

    <section id="our-team">
      <v-container class="mx-auto" style="margin: 0; padding: 0">
        <v-row>
          <v-col>
            <h1 class="text-center text-h4 text-sm-h3 font-weight-bold">
              Our Team
            </h1>
            <v-responsive class="mx-auto pt-2" width="56">
              <v-divider
                class="mb-1"
                style="background: whitesmoke"
              ></v-divider>
              <v-divider style="background: white"></v-divider>
            </v-responsive>
          </v-col>
        </v-row>
        <v-row justify="center">
          <TeamMember
            v-for="(
              { name, title, socials, description, innerimage }, i
            ) in team.slice(0, 1)"
            :key="i"
            :name="name"
            :title="title"
            :socials="socials"
            :description="description"
            :innerimage="innerimage"
          />
        </v-row>
        <v-row justify="center">
          <TeamMember
            v-for="(
              { name, title, socials, description, innerimage }, i
            ) in team.slice(1, 5)"
            :key="i"
            :name="name"
            :title="title"
            :socials="socials"
            :description="description"
            :innerimage="innerimage"
          />
        </v-row>
      </v-container>
      <div class="py-6"></div>
    </section>

    <!-- Five principles intro -->
    <section id="five-principles-intro">
      <v-container fluid style="padding: 0" class="hidden-xs-and-down">
        <v-divider style="background: grey"></v-divider>
        <!-- <span class="wavey__line"></span> -->

        <v-layout fill-height>
          <v-row no-gutters>
            <v-col cols="4">
              <v-container
                fill-height
                fluid
                style="
                  color: white;
                  background-image: linear-gradient(to top, blue, #3fa9f5);
                "
                class="rounded-r-xl"
              >
                <v-row>
                  <v-col align="left">
                    <v-lazy>
                      <div
                        class="text-subtitle-1 text-sm-h5 text-md-h4 text-uppercase font-weight-bold"
                      >
                        5 <br />
                        Issues
                      </div>
                    </v-lazy>
                  </v-col>
                </v-row>
                <v-row>
                  <v-col>
                    <v-lazy>
                      <div
                        class="text-subtitle-1 text-sm-h5 text-md-h4 text-uppercase font-weight-bold"
                      >
                        5 <br />
                        Principles
                      </div>
                    </v-lazy>
                  </v-col>
                </v-row>
                <v-row>
                  <v-col>
                    <v-lazy>
                      <div
                        class="text-subtitle-1 text-sm-h5 text-md-h4 text-uppercase font-weight-bold"
                      >
                        5 <br />
                        Outcomes
                      </div>
                    </v-lazy>
                  </v-col>
                </v-row>
              </v-container>
            </v-col>
            <div style="height: 75vh"></div>
            <v-col>
              <v-container
                class="d-flex justify-center ma-2"
                fill-height
                style="background: inherit"
              >
                <v-row no-gutters>
                  <v-col class="d-flex justify-center align-center">
                    <v-card
                      class="rounded text-center overflow-auto pa-10"
                      width="100%"
                      flat
                      style="background: whitesmoke; max-height: 100%"
                    >
                      <v-card-title
                        class="text-h4 text-sm-h3 font-weight-bold mb-3 text-uppercase text-left"
                        >Our <br />
                        Belief
                      </v-card-title>
                      <v-card-subtitle>
                        <v-responsive width="56">
                          <v-divider class="mb-1"></v-divider>
                          <v-divider></v-divider>
                        </v-responsive>
                      </v-card-subtitle>
                      <p
                        class="text-body-2 text-sm-body-1 text-lg-h6 font-weight-light pa-2 text-justify"
                      >
                        We believe in the
                        <strong>combined power of people and technology</strong>
                        as a means to tackle the ocean pollution problem, in
                        both education and actionable solutions. We realise the
                        importance of <strong>open-source technology</strong> as
                        it is free and accessible to all, which we believe is
                        the only way we will be able address our environmental
                        concerns efficiently.
                        <br />
                        <br />
                        Follow our <strong>5x5x5 framework</strong> to
                        understand how we generate impact, beginning with
                        identifying the key problems, then applying key pillar
                        principles, and finally creating solutions which lead to
                        impactful outcomes.
                        <br />
                      </p>
                    </v-card>
                  </v-col>
                </v-row>
                <v-row class="d-flex justify-center">
                  <v-col class="d-flex align-center justify-center">
                    <v-timeline
                      style="max-height: fit-content"
                      class="text-md-h6"
                      dense
                    >
                      <v-timeline-item icon="mdi-alert" fill-dot color="pink">
                        Identify the <br />
                        <strong> Key Issue</strong>
                      </v-timeline-item>
                      <v-timeline-item
                        icon="mdi-head-lightbulb-outline"
                        fill-dot
                        color="cyan"
                      >
                        Creating a solution via applying a <br />
                        <strong>Key Principle</strong>
                      </v-timeline-item>
                      <v-timeline-item icon="mdi-star" fill-dot>
                        Create <strong>Solution</strong> that brings an
                        <strong>Impactful Outcome</strong>
                      </v-timeline-item>
                    </v-timeline>
                  </v-col>
                </v-row>
              </v-container>
            </v-col>
          </v-row>
        </v-layout>
        <!-- <v-divider style="background: grey"></v-divider> -->
      </v-container>
    </section>

    <section id="five-principles">
      <div style="min-height: 100vh">
        <v-responsive>
          <v-img
            eager
            :src="require('assets/waves-background.png')"
            style="max-height: 25vh"
          ></v-img>
        </v-responsive>

        <v-container
          class="text-center text-h3 text-sm-h2 font-weight-bold mb-3 text-uppercase"
        >
          Five Framework
          <div class="py-1"></div>
          <v-responsive width="100" class="mx-auto">
            <v-divider class="mb-1" style="background: whitesmoke"></v-divider>
            <v-divider style="background: white"></v-divider>
          </v-responsive>
        </v-container>

        <div class="py-3"></div>
        <div>
          <SlidesPage></SlidesPage>
        </div>
      </div>
    </section>
    <div class="py-8"></div>
  </v-main>
</template>

<script>
// import SlidesPage from '../components/SlidesPage.vue'
export default {
  name: 'AboutPage',
  data() {
    return {
      window: 0,
      team: [
        {
          name: 'James Tcheng',
          title: 'Founder',
          socials: [
            { icon: 'mdi-facebook', link: 'https://www.facebook.com/' },
            { icon: 'mdi-instagram', link: 'https://www.instagram.com' },
            {
              icon: 'mdi-linkedin',
              link: 'https://www.linkedin.com/in/james-tcheng-834b1717a/',
            },
            { icon: 'mdi-github', link: 'https://github.com/doggie007' },
          ],
          description:
            "James Tcheng is a 17-year-old high school student studying in grade 12 at Eton College, UK.From a young age, James has witnessed the devastating effects of plastic pollution that surround the coastal areas of his hometown, Hong Kong. Deeply troubled by its detriment to human health and the public's lack of concern on the issue, he founded the organisation CyberWaves, an online platform that aims to raise awareness and create actionable solutions through sharing information and open-source solutions that tackle the problem. CyberWaves also strives to partner with ocean conservation organisations across the globe to equip them with technological tools such as machine learning and satellite imagery to aid in their efforts, which range from research to cleanups.",
          innerimage: 'james.jpg',
        },
        {
          name: 'Dhruvit Pindoria',
          title: 'Managing Director',
          socials: [
            { icon: 'mdi-instagram', link: 'https://www.instagram.com' },
            {
              icon: 'mdi-linkedin',
              link: 'https://www.linkedin.com/in/james-tcheng-834b1717a/',
            },
          ],
          description:
            'The environment has always been a keen interest of mine, running clubs since primary school. However, after visiting my home country of India frequently, the level of water pollution was incredibly high which inspired my urge to work on water conservation - an often overlooked issue when discussing the environment.',
          innerimage: 'dhruvit.png',
        },
        {
          name: 'Luca Matta',
          title: 'Operations Director',
          socials: [],
          description:
            "Luca is a 17-year-old student at Eton College, studying Maths, Further Maths, Physics, and Chemistry at A-Level. He wants to study Engineering at university and is passionate about using engineering to solve climate and environmental issues. He is a keen editor and writer, having founded Eton's environmental site theflorentina.com. He became interested in ocean conservation having watched Seaspiracy, and hopes to make a tangible impact through CyberWaves.",
          innerimage: 'luca_matta.jpg',
        },

        {
          name: 'Ptolemy Egan',
          title: 'Outreach Director',
          socials: [],
          description:
            'I am an academic scholar at a boarding school near London, but I come from East Anglia. My family has lived there for rather a long time and we feel a strong connection with the nature and landscape around us. As such, when walking or enjoying nature, I am disappointed to see littering, plastic waste, and environmental degradation. I have always been keen to safeguard what I have been privileged to grow up around, and am now eager to counter the risks to it face on. At school, I also play several sports, and so enjoy working in a team.',
          innerimage: 'dummy.jpg',
        },

        {
          name: 'Mokareoluwa Adewoye ',
          title: 'Development Director',
          socials: [],
          description:
            'Seeing the effects of overfishing and polluted waters in my hometown, I am empowered to make a difference through seeing the growth of this organisation.',
          innerimage: 'dummy.jpg',
        },
      ],
    }
  },
  head() {
    return {
      title: 'About',
      meta: [
        {
          hid: 'description',
          name: 'description',
          content:
            "Learn about CyberWave's mission and how we will achieve our goals.",
        },
      ],
    }
  },
}
</script>
