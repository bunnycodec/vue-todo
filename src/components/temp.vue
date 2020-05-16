<template>
  <div class="dashboard px-4">
    <h1 class="py-4 title grey--text text--darken-1">DASHBOARD</h1>

    <v-container class="py-12">

      <v-row class="mb-5 pa-3">
        <v-btn class="grey accent-1" @click="sortBy('title')">
          <v-icon left>mdi-folder</v-icon>
          <span class="caption text-capitalize">Sort By Title</span>
        </v-btn>
        <v-btn class="ml-3 grey accent-1" @click="sortBy('person')">
          <v-icon left>mdi-account</v-icon>
          <span class="caption text-capitalize">Sort By Person</span>
        </v-btn>
        <v-btn class="ml-3 grey accent-1" @click="sortBy('due')">
          <v-icon left>mdi-calendar</v-icon>
          <span class="caption text-capitalize">Sort By Date</span>
        </v-btn>
      </v-row>

      <v-card
        :class="`mb-1 project ${project.status}`"
        flat
        v-for="project in projects"
        :key="project.title"
      >
        <v-row class="pa-3">
          <v-col cols="12" sm="12" md="6">
            <div class="caption grey--text text--darken-2">Project Title</div>
            <div>{{project.title}}</div>
          </v-col>
          <v-col cols="6" sm="4" md="2">
            <div class="caption grey--text text--darken-2">Person</div>
            <div>{{project.person}}</div>
          </v-col>
          <v-col cols="6" sm="4" md="2">
            <div class="caption grey--text text--darken-2">Due by</div>
            <div>{{project.due}}</div>
          </v-col>
          <v-col cols="6" sm="4" md="2">
            <div class="float-right">
              <v-chip small :color="changeColor(project.status)" class="white--text my-2 caption text-uppercase">{{project.status}}</v-chip>
            </div>
          </v-col>
        </v-row>
      </v-card>
    </v-container>
  </div>
</template>

<script>
export default {
  data() {
    return {
      projects: [
        {
          title: "Web Development Project",
          person: "Sunny Kumar",
          due: "1st Feb 2020",
          status: "ongoing"
        },
        {
          title: "Front End Design",
          person: "Evan You",
          due: "21st Jan 2020",
          status: "complete"
        },
        {
          title: "Machine Learning",
          person: "John Mark",
          due: "23rd June 2019",
          status: "complete"
        },
        {
          title: "Artificial Intelligence",
          person: "Steve Rogers",
          due: "12th Oct 2019",
          status: "overdue"
        }
      ]
    }
  },
  methods: {
    changeColor(value) {
      if (value === "ongoing") return "amber darken-1";
      else if (value === "complete") return "green";
      else return "red";
    },

    sortBy(value) {
      this.projects.sort((a, b) => a[value] < b[value] ? -1 : 1);
    }
  }
};
</script>

<style lang="scss">
.project.ongoing {
  border-left: 0.5rem solid #dc9e82;
}
.project.complete {
  border-left: 0.5rem solid #458868;
}
.project.overdue {
  border-left: 0.5rem solid #bb0a21;
}
</style>