<template>
  <v-app id="inspire">
    <v-navigation-drawer 
      v-model="drawer"
      app
    >
      <v-list-item>
        <v-list-item-content>
          <v-list-item-title class="text-h6">
            <img alt="Foundry logo icon" src="./assets/logo-full.png" style="width: 80%"/>
          </v-list-item-title>
          
        </v-list-item-content>
      </v-list-item>
      <v-divider></v-divider>

      <v-list
        dense
        nav
      >
        <v-list-item
          v-for="item in items"
          :key="item.title"
          :to="item.to"
          link
        >
          <v-list-item-icon>
            <v-icon>{{ item.icon }}</v-icon>
          </v-list-item-icon>

          <v-list-item-content>
            <v-list-item-title>{{ item.title }}</v-list-item-title>
          </v-list-item-content>
        </v-list-item>
      </v-list>
    </v-navigation-drawer>

    <v-app-bar app>
      <v-app-bar-nav-icon @click="drawer = !drawer"></v-app-bar-nav-icon>

      <!-- <v-toolbar-title> <img alt="Foundry logo icon" src="./assets/logo-icon.png" style="width: 40px"/></v-toolbar-title> -->
    </v-app-bar>

    <v-main>
      <router-view></router-view>
    </v-main>
  </v-app>
</template>

<script>
  export default {
    data: () => ({ drawer: null,
    items: [
          { title: 'Home', icon: 'mdi-home', to:'/' },
          { title: 'Datasets', icon: 'mdi-magnify', to:'/datasets' },
          { title: 'About', icon: 'mdi-help-box', to:'/about' },
          { title: 'Documentation', icon: 'mdi-file-document-multiple-outline'},
          { title: 'Examples', icon: 'mdi-rocket-launch' }
        ] }),
  }
</script>