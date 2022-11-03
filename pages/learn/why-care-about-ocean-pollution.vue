<template>
  <v-main>
    <v-container class="mt-10">
      <v-row class="pa-1" justify="start">
        <v-btn elevation="2" rounded class="mx-1" small nuxt to="/learn"
          ><v-icon>mdi-keyboard-backspace</v-icon>Back</v-btn
        >
      </v-row>
      <v-row align="center" justify="center">
        <div class="text-center">
          <p class="subtitle-2">September 20, 2022</p>

          <p class="text-h4 font-weight-bold">
            Why You Must Care About Ocean Pollution
          </p>
          <p class="subtitle-1 font-weight-medium">Author: Luca Matta</p>
        </div>
      </v-row>
      <v-divider></v-divider>
      <div class="py-4"></div>
      <v-row id="body" class="mx-2 text-body-1">
        <p
          class="text-subtitle-1 font-weight-medium font-italic mt-4 mb-8 text-justify"
        >
          <v-card
            tile
            outlined
            class="rounded-lg pa-2"
            style="background-color: whitesmoke"
          >
            Ocean pollution is one of the most widespread dangers to
            <strong>human health</strong>, a key contributor to
            <strong>global warming</strong>, and of course,
            <strong>destroying marine life</strong>. Yet, it continues to get
            worse as pollution accumulates in oceans globally, and the extent of
            the damage is largely misunderstood.
          </v-card>
        </p>
        <v-img
          :src="require('assets/plastic-ocean.jpg')"
          max-height="550"
        ></v-img>

        <p class="mt-8">
          <strong>12 million tonnes</strong> of plastic enter the oceans each
          year, which then gathers in coast sediments as well as the deep-sea,
          where currents come together. This results in giant
          <strong>'garbage patches'</strong>, such as the Great Pacific Garbage
          Patch, which covers an area twice the size of Texas. By 2050, ocean
          plastic will outweigh all of the oceans' fish. <br />
          <br />
          We regularly hear about the impact of our plastic waste but ocean
          pollution also includes toxic metals, manufactured chemicals, crude
          oil, urban and industrial waste, pesticides, fertilisers,
          pharmaceutical chemicals, sewage and agricultural runoff. 80% of ocean
          pollution arises from sources on land, reaching the ocean through
          rivers, runoff, deposition from the atmosphere, direct dumping.
        </p>
        <p class="mt-4 mb-8">
          Plastics that enter the oceans mostly break down into
          <strong>microplastics</strong> by sun exposure and wave action.
          Microplastics contain many toxic chemicals such as
          <strong>carcinogens</strong> (cancer causing)
          <strong>endocrine disruptors</strong>
          (interfering with hormones) and others that can reduce fertility and
          more. They enter the food chain as they accumulate in fish and other
          marine animals, which are then eaten by humans.
          <br /><br />
          Mercury is another common ocean pollutant, from coal burning and gold
          mining. Mercury contaminates predatory fish such as tuna to a great
          extent, which can cause <strong>birth defects</strong> if eaten by
          expectant mothers, such as heart disease, brain damage and increased
          risk of learning disabilities.
        </p>
        <v-img
          :src="require('assets/fish-microplastics.jpg')"
          max-height="550"
        ></v-img>
        <p class="mt-8 mb-4">
          The effects to human health are not the only concern surrounding ocean
          pollution. Our oceans act as the
          <strong>largest natural carbon sink</strong>. However, plastic
          pollution is threatening this. Not only does it choke marine animals,
          sunlight and heat also cause the plastic to release greenhouse gases
          and the planet to warm up, leading to a vicious circle as the cycle
          perpetuates. Oil spills are another way that ocean pollution
          <strong>perpetuates climate change</strong>. Petroleum threatens
          marine microorganisms by inhibiting their capacity for photosynthesis
          as blocks their access to sunlight. This is detrimental to the climate
          as photosynthesis converts atmospheric carbon dioxide (a greenhouse
          gas) into oxygen.
        </p>
        <p class="my-4">
          Despite the overwhelming evidence,
          <strong
            >many people are still skeptical as to whether ocean pollution
            exists and/or is a threat</strong
          >. This is mainly due to the fact that waste in the USA and other
          countries is shipped offshore for developing countries to deal with,
          so it is seen on a much smaller scale. Furthermore, the effect of
          microplastics on human health is only beginning to be seen.
          Stakeholders in relevant industries such as fishing do not want their
          demand, and thus profits, to decrease and so deny the impacts of ocean
          pollution.
        </p>
        <p class="mt-8 text-subtitle-1 font-weight-bold">
          <strong>CyberWaves</strong> is a group of teenage environmentalists
          who are committed to protecting our oceans primarily from ocean
          pollution and the climate crisis. Through sharing and explaining
          technology used by environmental scientists which educates about and
          tackles these problems, we hope to one day empower other organisations
          and communities to be technologically equipped when facing the
          challenge of ocean pollution themselves and improve scientific
          communication of these problems. <br />
          <br />
          This is particularly important as it is often small communities
          without technological expertise dealing with the impacts of the
          pollution. One of the main ways we hope to do this is open-source
          technology, a free and accessible way of teach on this problem and
          allow people to tackle ocean pollution efficiently. Ultimately, we
          hope to raise awareness on the topic and inspire collective action.
        </p>
      </v-row>
    </v-container>
    <div class="py-4"></div>
  </v-main>
</template>

<style scoped>
strong {
  color: rgb(15, 23, 171);
}
</style>
<script>
export default {
  name: 'Child',
}
</script>
