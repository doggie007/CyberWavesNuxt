<template>
  <!-- <ComingSoon></ComingSoon> -->
  <v-main>
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
            "Learn about CyberWave's mission and how we will achieve our goals.",
        },
      ],
    }
  },
  components: { Feed },
}
</script>
