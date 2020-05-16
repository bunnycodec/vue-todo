<template>
  <div class="team px-4">
    <h1 class="py-4 title grey--text text--darken-1">TEAM</h1>

    <v-container class="py-12">
      <v-row>
        <v-col v-for="person in team" :key="person.role" lg="3" md="4" sm="6" cols="12">
          <v-card elevation="24" flat class="pa-3 text-center" color="#bdbdbd">
            <v-responsive class="py-5">
              <v-avatar size="200">
                <img :src="require('../assets/' + person.avatar)" />
              </v-avatar>
            </v-responsive>
            <div class="py-6">
              <div class="headline black--text">{{person.name}}</div>
              <div class="subheading-1 grey--text text--darken-2">{{person.role}}</div>
            </div>
            <v-card-actions>
              <v-btn elevation="10" color="#bdbdbd">
                <v-icon left>mdi-message</v-icon>
                <span>Message</span>
              </v-btn>
            </v-card-actions>
          </v-card>
        </v-col>
      </v-row>
    </v-container>
  </div>
</template>

<script>
export default {
  data() {
    return {
      team: [
        { name: "Sunny Kumar", role: "Web Developer", avatar: 'img2.png' },
        { name: "Steffin Abraham", role: "Graphic Designer", avatar: 'img2.png' },
        { name: "Tana Joji", role: "Stunt Rider", avatar: 'img.png' },
        { name: "Manoj Kumar", role: "Coroporate Trainer", avatar: 'img2.png' }
      ]
    };
  }
};
</script>
