<template>
  <v-app id="inspire">
    <!-- mobile nav -->
    <v-navigation-drawer disable-resize-watcher v-model="drawer" app null class="d-xl-none d-lg-none d-md-none">
      <img alt="Foundry logo icon" src="./assets/logo-full.png" style="width: 200px" />
      <v-divider></v-divider>
      <v-list dense nav>
        <v-list-item v-for="item in items" :key="item.title">
          <a :href="item.to" class="text-decoration-none grey--text text--darken-2">
            <v-list-item-icon class="d-inline">
              <v-icon class="d-inline" color="indigo lighten-1 ">{{ item.icon }}</v-icon>
            </v-list-item-icon>
            <v-list-item-content class="d-inline">
              <v-list-item-title class="d-inline">{{ item.title }}</v-list-item-title>
            </v-list-item-content>
          </a>
        </v-list-item>
      </v-list>
    </v-navigation-drawer>

    <v-app-bar app color="white">
      <v-app-bar-nav-icon class="d-md-none d-lg-none d-xl-none" @click="drawer = !drawer"></v-app-bar-nav-icon>
      <!-- desktop nav bar -->
      <a href="/" class="d-none d-md-flex">
        <v-toolbar-title>
          <img alt="Foundry logo icon" src="./assets/logo-full.png" style="width: 200px" />
        </v-toolbar-title>
      </a>

      <v-spacer class="d-none d-md-flex"></v-spacer>

      <v-toolbar-items class="d-none d-md-flex" v-for="item in items"
        :key="item.title" :to="item.to" link>
        <a :href="item.to" class="text-decoration-none indigo--text text--darken-1 ">
          <v-toolbar-title class="mx-4 mt-4 text-body-1">{{ item.title }}</v-toolbar-title>
        </a>
      </v-toolbar-items>
    </v-app-bar>


    <v-main>
      <router-view></router-view>
    </v-main>
  </v-app>
</template>

<script>
export default {
  data: () => ({
    drawer: false,
    items: [
      { title: 'Home', icon: 'mdi-home', to: '/' },
      { title: 'Datasets', icon: 'mdi-magnify', to: '#/datasets' },
      { title: 'Documentation', icon: 'mdi-file-document-multiple-outline', to: 'https://ai-materials-and-chemistry.gitbook.io/foundry/v/docs/' },
      { title: 'Examples', icon: 'mdi-rocket-launch', to: `https://github.com/MLMI2-CSSI/foundry/tree/main/examples` }
    ]
  }),
}
</script>