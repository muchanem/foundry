<template>
  <div class="about">
    <!-- "We are Foundry" section-->
    <v-sheet class="text-center py-10 col-12 py-12" color="red lighten-4" elevation="12">
      <v-sheet rounded="xl" color="red lighten-5" class="col-md-9 col-11 mx-auto mt-12 py-4" elevation="5">
        <h1 class="text-h2 col-sm-10 col-12 mx-auto ">
          We are Foundry
        </h1>
        <h2 class="font-weight-regular indigo--text">
          We make using and sharing models and datasets easy
        </h2>
      </v-sheet>
    </v-sheet>
    <!-- End of "We are Foundry" section -->

    <!-- Middle explaination section-->
    <div class="mt-12 px-md-10 px-1">
      <h2 class="text-center font-weight-regular my-12">
        We believe Accessibility, Community, and Collaboration are the keys to accelerating research.
      </h2>
      <v-row class="mt-8">
        <v-sheet rounded="xl" class="col-md-3 col-11 mx-auto pa-5 mt-2" elevation="5">
          <h3 class="mb-4 text-center">Accessibility</h3>
          <p>
            Foundry simplifies your workflow by hosting large interpretable
            datasets and ready-to-use models. We remove common barriers for
            using machine learning so you can get right to work on your
            research. Reproducing models and using large datasets has never
            been easier.
          </p>
        </v-sheet>
        <v-sheet rounded="xl" class="col-md-3 col-11 mx-auto pa-5 mt-2" elevation="5">
          <h3 class="mb-4 text-center">Community</h3>
          <p>
            We strive to connect like-minded people to drive research forward.
            Whether you're a scientist who would like to use machine learning
            but doesn't know where to start, or a software engineer looking to
            apply your machine learning knowledge, we have a space for you in
            our community.
          </p>
        </v-sheet>
        <v-sheet rounded="xl" class="col-md-3 col-11 mx-auto pa-5 mt-2" elevation="5">
          <h3 class="mb-4 text-center">Collaboration</h3>
          <p>
            Sharing data and models is more important now than ever. As the
            reproducibility crisis in science continues to limit research, we
            see Foundry as the ultimate collaborative tool to combat it. We
            host large datasets that can be loaded from anywhere and models
            that are run on our service so there are no computing power
            requirements for you.
          </p>
        </v-sheet>
      </v-row>
    </div>


    <!-- TEAM SECTION -->
    <h2 class="text-center mt-12 py-5">
      Team
    </h2>
    <v-row>
      <v-card class="mx-auto mt-5" max-width="344" v-for="member in team" :key="member.name">
        <v-img src="https://cdn.vuetifyjs.com/images/cards/sunshine.jpg" height="200px"></v-img>

        <v-card-title>
          {{ member.name }}
        </v-card-title>

        <v-card-subtitle>
          {{ member.institution }}
        </v-card-subtitle>


      </v-card>
    </v-row>

  </div>
</template>

<script>

export default {
  name: 'About',
  data: () => ({
    team: [
      { name: 'Ben', institution: 'meow' },
      { name: 'Ari', institution: 'hi' },
      { name: 'KJ', institution: 'no' }]
  }),
}
</script>
  