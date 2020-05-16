<template>
  <nav>
    <v-app-bar flat app style="background: #010c21;">
      <v-app-bar-nav-icon
        @click="drawer = !drawer"
        class="grey--text mr-4"
        style="background: #010c21;"
      ></v-app-bar-nav-icon>
      <v-toolbar-title class="teal--text headline">
        <span class="headline mr-1">TODO</span>
        <span class="subtitle-1 font-weight-light">CODEC</span>
      </v-toolbar-title>

      <v-spacer></v-spacer>

      <v-menu offset-y>
        <template v-slot:activator="{ on }">
          <v-btn flat text color="grey" v-on="on">
            <span>Menu</span>
            <v-icon>mdi-menu</v-icon>
          </v-btn>
        </template>
        <v-list>
          <v-list-item v-for="link in links" :key="link.icon" router :to="link.route">
            <v-list-item-title>{{link.text}}</v-list-item-title>
          </v-list-item>
        </v-list>
      </v-menu>

      <v-btn text flat color="grey">
        <span>Sign out</span>
        <v-icon>mdi-logout</v-icon>
      </v-btn>
    </v-app-bar>
    <v-navigation-drawer v-model="drawer" app src class="blue-grey darken-3">
      <v-row class="mt-10 text-center">
        <v-col cols="12">
          <v-avatar size="150">
            <img src="../assets/img.png" alt />
          </v-avatar>
        </v-col>
        <v-col cols="12">
          <div class="white--text headline">Tana Joji</div>
        </v-col>
        <v-col cols="12" class="my-8">
          <popup />
        </v-col>
      </v-row>

      <v-list>
        <v-list-item v-for="(link, index) in links" :key="index" router :to="link.route">
          <v-list-item-icon>
            <v-icon class="white--text">{{link.icon}}</v-icon>
          </v-list-item-icon>
          <v-list-item-content>
            <v-list-item-title class="white--text">{{link.text}}</v-list-item-title>
          </v-list-item-content>
        </v-list-item>
      </v-list>
    </v-navigation-drawer>
  </nav>
</template>

<script>
import Popup from "./Popup.vue";

export default {
  components: {
    Popup
  },
  data() {
    return {
      drawer: false,
      links: [
        { icon: "mdi-view-dashboard", text: "Dashboard", route: "/" },
        { icon: "mdi-folder", text: "My Projects", route: "/projects" },
        { icon: "mdi-account", text: "Team", route: "/team" }
      ]
    };
  }
};
</script>