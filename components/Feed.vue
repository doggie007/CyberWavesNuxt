<template>
  <v-container>
    <v-row align="center" justify="center">
      <feed-card
        v-for="(article, i) in articles"
        :key="article.title"
        :size="layout[i]"
        :value="article"
      />
    </v-row>
  </v-container>
</template>

<script>
import FeedCard from './FeedCard.vue'
export default {
  name: 'Feed',
  components: { FeedCard },
  data() {
    return {
      layout: [2, 2],
      articles: [
        {
          title: 'Why You Must Care About Ocean Pollution',
          author: 'Luca Matta',
          category: 'General',
          hero: 'plastic-ocean.jpg',
          date: '20/9/2022',
          description:
            'Ocean pollution is one of the most widespread dangers to human health, a key contributor to global warming, and of course, destroying marine life. Yet, it continues to get worse as pollution accumulates in oceans globally, and the extent of the damage is largely misunderstood...',
          link: '/learn/why-care-about-ocean-pollution',
        },
        // {
        //   title: 'Swedish Fishing',
        //   author: 'Rachel L',
        //   category: 'Leisure',
        //   hero: 'autumnclouds.jpg',
        //   date: '27/10/2022',
        //   description:
        //     'Lorem ipsum dolor sit amet consectetur adipisicing elit. Tempore quos, magnam aperiam mollitia natus libero beatae nulla dolore dolorum non sint, adipisci saepe esse nostrum quas commodi labore! Laboriosam, minima!',
        // },
      ],
    }
  },
}
</script>
