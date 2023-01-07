<template>
  <!-- <ComingSoon></ComingSoon> -->
  <v-main>
    <h1>WaveScope</h1>
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
