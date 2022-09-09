<template>
  <div class="about">
    <!-- "We are Foundry" section-->
    <v-sheet class="text-center col-12 py-12" color="indigo lighten-2" elevation="12">
      <h1 class="text-h2 col-sm-10 col-12 mx-auto white--text mt-10">
        We are Foundry
      </h1>
      <h2 class="font-weight-regular blue-grey--text text--lighten-5 mb-12">
        Simplifying your machine learning workflow

      </h2>

    </v-sheet>
    <!-- End of "We are Foundry" section -->

    <!-- Middle explaination section-->
    <div class="mt-12 px-md-10 px-1">
      <h2 class="text-center font-weight-regular mt-12 mb-12 col-md-7 mx-auto">
        We believe Accessibility, Reproducibility, and Collaboration are the keys to accelerating research.
      </h2>
      <v-row class="mt-8">
        <v-sheet rounded="xl" color="indigo lighten-5" class="col-md-3 col-11 mx-auto pa-5 mt-5" elevation="5">
          <h3 class="mb-4 text-center indigo--text">Accessibility</h3>
          <p>
            Foundry simplifies your workflow by hosting large interpretable
            datasets and ready-to-use models. We remove common barriers for
            using machine learning so you can get right to work on your
            research. Reproducing models and using large datasets has never
            been easier.
          </p>
        </v-sheet>
        <v-sheet rounded="xl" color="red lighten-5" class="col-md-3 col-11 mx-auto pa-5 mt-5" elevation="5">
          <h3 class="mb-4 text-center red--text text--lighten-2">Reproducibility</h3>
          <p>
            The reproducibility crisis, an ongoing crisis in the scientific community in which many studies are
            difficult or impossible to replicate or reproduce, limits research. Foundry makes replicating work almost
            trivial.
          </p>
        </v-sheet>
        <v-sheet rounded="xl" color="indigo lighten-5" class="col-md-3 col-11 mx-auto pa-5 mt-5" elevation="5">
          <h3 class="mb-4 text-center indigo--text">Collaboration</h3>
          <p>
            Sharing data and models can be a huge pain point when these files are too large to share easily in common
            infrastructures. Foundry’s infrastructure is built with this in mind. We
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
        <v-img :src="member.img" height="200px"></v-img>

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
      { name: 'Ben Blaiszik', institution: 'University of Chicago and Argonne National Lab', img: require('.././assets/ben.jpeg') },
      { name: 'Dane Morgan', institution: 'University of Wisconsin-Madison', img: require('.././assets/dane.jpeg') },
      { name: 'Paul Voyles', institution: 'University of Wisconsin-Madison', img: require('.././assets/paul.jpeg') }]
  }),
}
</script>
  