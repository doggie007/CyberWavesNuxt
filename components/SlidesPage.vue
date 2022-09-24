<template>
  <v-container>
    <v-row>
      <v-card tile>
        <v-card-actions class="justify-space-between">
          <v-btn text @click="prev">
            <v-icon>mdi-chevron-left</v-icon>
          </v-btn>
          <v-item-group v-model="onboarding" class="text-center" mandatory>
            <v-row>
              <v-col v-for="(item, n) in fiveFramework" :key="`btn-${n}`">
                <v-item v-slot="{ active, toggle }" class="px-auto">
                  <v-btn icon small :input-value="active" @click="toggle">
                    <!-- <v-icon>mdi-record</v-icon> -->
                    {{ n + 1 }}
                  </v-btn>
                </v-item>
              </v-col>
            </v-row>
          </v-item-group>
          <v-btn text @click="next">
            <v-icon>mdi-chevron-right</v-icon>
          </v-btn>
        </v-card-actions>
        <v-window v-model="onboarding" vertical>
          <SlidesItem
            v-for="(item, i) in fiveFramework"
            :key="`card-${i}`"
            :item="item"
            :number="i"
          ></SlidesItem>
        </v-window>
      </v-card>
    </v-row>
  </v-container>
</template>

<script>
import SlidesItem from './SlidesItem.vue'
export default {
  data: () => ({
    length: 5,
    onboarding: 0,
    fiveFramework: [
      {
        issue: 'Human Psychology',
        issueDescription:
          'Psychology can no doubt account for general disengagement in mitigating environmental impacts, and ocean plastic pollution is one of them. Centuries of temporal discounting means that it is difficult to see the dangers this problem will lead to in the coming decades and makes short-term behavioural change difficult, causing the un-ending cycle of plastic creation and waste.',
        principle: 'Encourage Learning',
        principleDescription:
          'Through education, we can overcome our instinctive thoughts and be nudged towards thinking more about the pressing issue more.',
        outcome:
          'Engaging approach to ocean pollution education that raises awareness',
        outcomeDescription:
          'Educational materials combined with an interactive approach made available through technology can lead to greater information retention, causing people to be conscious of their own actions and spread awareness within communities.',
      },
      {
        issue: 'Lack of technological usage',
        issueDescription:
          'Many organisations and communities around the world do not have the technological resources and manpower to solve the ocean pollution problem efficiently. Some might not realise the power of technology in the combat to this problem.',
        principle: 'Share open-source technology',
        principleDescription:
          'We believe in the power of technology to tackle the problem in the best and most efficient manner.',
        outcome: 'Provide applications which enable change',
        outcomeDescription:
          'Through sharing, people are empowered with the knowledge required to tackle the problem themselves and organisations can capitalise from state-of-the-art technology to reduce ocean pollution.',
      },
      {
        issue: 'Feasibility of Problem Solving',
        issueDescription:
          ' fatalism is important in consideration with any environmental problem given these problems are occurring on a global scale. The fact that avoiding the use of plastics is essentially impossible in modern life, it is easy to believe individual actions make no impact.',
        principle: 'Foster Changes in Attitudes',
        principleDescription:
          'Lorem ipsum dolor, sit amet consectetur adipisicing elit. Quis excepturi labore similique repellat aspernatur? Cumque corrupti quod debitis et ex illum, eum ducimus totam blanditiis eius, natus deserunt nesciunt veritatis?',
        outcome: 'Developing a personal connection to the problem',
        outcomeDescription:
          'Lorem ipsum dolor, sit amet consectetur adipisicing elit. Quis excepturi labore similique repellat aspernatur? Cumque corrupti quod debitis et ex illum, eum ducimus totam blanditiis eius, natus deserunt nesciunt veritatis?',
      },
      {
        issue: 'Knowledge Translation',
        issueDescription:
          'Lorem ipsum dolor, sit amet consectetur adipisicing elit. Quis excepturi labore similique repellat aspernatur? Cumque corrupti quod debitis et ex illum, eum ducimus totam blanditiis eius, natus deserunt nesciunt veritatis?',
        principle: 'Maintain Transparency',
        principleDescription:
          'Lorem ipsum dolor, sit amet consectetur adipisicing elit. Quis excepturi labore similique repellat aspernatur? Cumque corrupti quod debitis et ex illum, eum ducimus totam blanditiis eius, natus deserunt nesciunt veritatis?',
        outcome: 'Provide transparency and combat mistrust about its dangers ',
        outcomeDescription:
          'Lorem ipsum dolor, sit amet consectetur adipisicing elit. Quis excepturi labore similique repellat aspernatur? Cumque corrupti quod debitis et ex illum, eum ducimus totam blanditiis eius, natus deserunt nesciunt veritatis?',
      },
      {
        issue: 'Scepticism',
        issueDescription:
          'Lorem ipsum dolor, sit amet consectetur adipisicing elit. Quis excepturi labore similique repellat aspernatur? Cumque corrupti quod debitis et ex illum, eum ducimus totam blanditiis eius, natus deserunt nesciunt veritatis?',
        principle: 'Promote Youth Engagement',
        principleDescription:
          'Lorem ipsum dolor, sit amet consectetur adipisicing elit. Quis excepturi labore similique repellat aspernatur? Cumque corrupti quod debitis et ex illum, eum ducimus totam blanditiis eius, natus deserunt nesciunt veritatis?',
        outcome:
          'Youth engagement and advocacy development to inspire collective intergenerational action',
        outcomeDescription:
          'Lorem ipsum dolor, sit amet consectetur adipisicing elit. Quis excepturi labore similique repellat aspernatur? Cumque corrupti quod debitis et ex illum, eum ducimus totam blanditiis eius, natus deserunt nesciunt veritatis?',
      },
    ],
  }),
  methods: {
    next() {
      this.onboarding =
        this.onboarding + 1 === this.length ? 0 : this.onboarding + 1
    },
    prev() {
      this.onboarding =
        this.onboarding - 1 < 0 ? this.length - 1 : this.onboarding - 1
    },
  },
  components: { SlidesItem },
}
</script>
