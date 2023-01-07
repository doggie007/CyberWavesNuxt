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
        issue: 'NGOs & Organisations Lack Advanced Technological Support',
        issueDescription:
          'Many organisations and communities around the world do not have the technological resources and manpower to solve the ocean pollution problem efficiently. Some might not realise the power of technology in the combat to this colossal problem.',
        principle: 'Provide Publicly Accessible Technology',
        principleDescription:
          'We believe in the power of technology to tackle the problem in the best and most efficient manner. Importantly, state-of-the-art technology must be shared freely and openly for all to utilize.',
        outcome:
          'Support NGOs & Organisations with the Technology to Empower Change',
        outcomeDescription:
          'Through sharing, organizations are empowered to tackle the problem can can capitalise from state-of-the-art technology to maximize their efforts to tackle ocean pollution. SPLASTIC provides coastal cleanup organizations with a list of the most optimal places to conduct cleanup efforts to maximize the use of their human resources.',
      },
      {
        issue: 'Human Psychology',
        issueDescription:
          'Psychology can no doubt account for general disengagement in mitigating environmental impacts, and ocean plastic pollution is one of them. Centuries of temporal discounting means that it is difficult to see the dangers this problem will lead to in the coming decades and makes short-term behavioural change difficult, causing the un-ending cycle of plastic creation and waste.',
        principle: 'Nudge Behaviour through Effective Learning',
        principleDescription:
          'Through education, we can overcome our instinctive thoughts and be nudged towards thinking more about the pressing issue more. However, simply showing facts and figures is insufficient to overcome psychological biases.',
        outcome: 'Engaging Approach that Raises Awareness Effectively',
        outcomeDescription:
          'Educational materials combined with an interactive approach made available through technology can lead to greater information retention, causing people to be conscious of their own actions and spread awareness within communities. SEAVISION aims to visualize the ocean pollution problem by mapping out where plastic patches exist, while SPLASTIC offers an interactive way of seeing how pollution moves in our oceans.',
      },
      {
        issue: 'Global-Scale Problem',
        issueDescription:
          'Fatalism is important in consideration with any environmental problem given these problems are occurring on a global scale. The fact that avoiding the use of plastics is essentially impossible in modern life, it is easy to believe individual actions make zero impact when believing most people are free-riders. This makes it difficult to enforce behavioral changes and incentivize volunteering for ocean conservations activities.',
        principle: 'Foster Changes in Attitudes',
        principleDescription:
          'We believe that by shifting perspectives, focusing on how indivdual impact are still impacts and conveying the impact of small-scale activities, attitudes towards solving this colossal problem will change for the better.',
        outcome: 'Emphasize Small-Scale Impact',
        outcomeDescription:
          'Using a combined approach of showing the impact of small-scale NGO activities with SEAVISION and our blog WAVESCOPE that inspire new ways of looking at how to individually solve ocean pollution, we aim to shift perspectives about the issue.',
      },
      {
        issue: 'Knowledge Translation',
        issueDescription:
          "Scientific knowledge is oftentimes too complicated or takes too long to understand, which only confuses the public and has no effect on people. Media often help bring scientists' core message to the public, but offer very little detailed information that causes mistrust. It seems that this is a signficant gap when transferring knowledge to the public effectively.",
        principle: 'Maintain Transparency',
        principleDescription:
          'By making it clear how information is discovered in an understandable way, we believe it can close this "knowledge translation gap" and combat mistrust.',
        outcome: 'Provide Clear & Concise Explanations',
        outcomeDescription:
          'For our products, we provide explanations to explain how these products work in the background, with concision while providing sufficient detail.',
      },
      {
        issue: 'Lack of Youth Community Participation',
        issueDescription:
          'Young people in this generation will grow into an era where environmental issues are extremely visible, whether it be sinking of major cities due to climate change or the extinction of marine species because of long-term plastic pollution effects. However, many teens are still not engaging with these pressing problems.',
        principle: 'Promote Youth Engagement & Advocacy Development',
        principleDescription:
          'Spreading the news to youth and targeting youth engagement can build a generation of changemakers who start from this day to prevent environmental disasters from happening in the next several decades.',
        outcome:
          'Appeal to Youth Audience to Inspire Collective Intergenerational Action',
        outcomeDescription:
          'Founded by a team of youth, we know exactly how to get them excited. Technology is the key way we believe can excite our younger audience.',
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
