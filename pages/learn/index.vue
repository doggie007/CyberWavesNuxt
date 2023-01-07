<template>
  <!-- <ComingSoon></ComingSoon> -->
  <v-main>
    <div class="text-center">
      <v-responsive>
        <v-img
          eager
          :src="require('assets/waves-background.png')"
          style="max-height: 25vh"
        ></v-img>
      </v-responsive>
      <h1 class="text-h2">WaveScope</h1>

      <v-responsive class="mx-auto mb-8 pt-3" width="100">
        <v-divider class="mb-1"></v-divider>
        <v-divider></v-divider>
      </v-responsive>
      <p class="text-subtitle-1">
        WaveScope: The CyberWaves Blog containing information ranging from ocean
        pollution misconceptions to how our products work!
      </p>
      <div class="py-6"></div>
    </div>
    <Feed></Feed>
  </v-main>
</template>
<script>
import Feed from '@/components/Feed.vue'
// import ComingSoon from './coming-soon.vue'
export default {
  name: 'LearnPage',
  head() {
    return {
      title: 'Learn',
      meta: [
        {
          hid: 'description',
          name: 'description',
          content:
            "Learn about CyberWave's Mission and how we will achieve our goals, as well as vital information about the ocean pollution problem.",
        },
      ],
    }
  },
  components: { Feed },
}
</script>
