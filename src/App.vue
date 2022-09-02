<template>
  <v-app id="inspire">

    <!-- desktop nav bar -->
    <v-toolbar class="flex-grow-0 d-none d-md-block">
      <a href="/">
        <v-toolbar-title>
          <img alt="Foundry logo icon" src="./assets/logo-full.png" style="width: 200px" />
        </v-toolbar-title>
      </a>

      <v-spacer></v-spacer>

      <v-toolbar-items v-for="item in items" :key="item.title" :to="item.to" link>
        <a :href="item.to" class="text-decoration-none indigo--text darken-1 ">
          <v-toolbar-title class="mx-4 mt-4 text-body-1">{{ item.title }}</v-toolbar-title>
        </a>
      </v-toolbar-items>
    </v-toolbar>
    <!-- end of desktop nav bar -->

    <!-- start of mobile nav bar -->


    <!-- end of mobile nav bar -->

    <v-main>
      <router-view></router-view>
    </v-main>
  </v-app>
</template>

<script>
export default {
  data: () => ({
    drawer: null,
    items: [
      { title: 'Home', icon: 'mdi-home', to: '/' },
      { title: 'Datasets', icon: 'mdi-magnify', to: '#/datasets' },
      { title: 'Documentation', icon: 'mdi-file-document-multiple-outline', to: 'https://ai-materials-and-chemistry.gitbook.io/foundry/v/docs/' },
      { title: 'Examples', icon: 'mdi-rocket-launch', to: `https://github.com/MLMI2-CSSI/foundry/tree/main/examples` }
    ]
  }),
}
</script>