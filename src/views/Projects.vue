<template>
  <div class="projects px-4">
    <h1 class="py-4 title grey--text text--darken-1">PROJECTS</h1>

    <v-container class="py-12">
      <v-expansion-panels>
        <v-expansion-panel class="pa-2 grey lighten-1" v-for="(project,i) in myProjects" :key="i">
          <v-expansion-panel-header class="headline font-weight-light">{{project.title}}</v-expansion-panel-header>
          <v-expansion-panel-content>
            <div class="grey--text text--darken-3 title font-weight-bold">Due : {{project.due}}</div>
            <div class="grey--text text--darken-2 body-1 mt-1">{{project.content}}</div>
          </v-expansion-panel-content>
        </v-expansion-panel>
      </v-expansion-panels>
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
          due: "2020-02-01",
          status: "ongoing",
          content:
            "Lorem ipsum dolor sit, amet consectetur adipisicing elit. Repudiandae rerum, delectus ullam molestias dicta eos minus laborum consequuntur? Dolor consequuntur ab error amet quos excepturi voluptatum nesciunt accusamus eum quidem."
        },
        {
          title: "Front End Design",
          person: "Evan You",
          due: "2020-01-21",
          status: "complete",
          content:
            "Lorem ipsum dolor sit, amet consectetur adipisicing elit. Repudiandae rerum, delectus ullam molestias dicta eos minus laborum consequuntur? Dolor consequuntur ab error amet quos excepturi voluptatum nesciunt accusamus eum quidem."
        },
        {
          title: "Machine Learning",
          person: "John Mark",
          due: "2019-06-23",
          status: "complete",
          content:
            "Lorem ipsum dolor sit, amet consectetur adipisicing elit. Repudiandae rerum, delectus ullam molestias dicta eos minus laborum consequuntur? Dolor consequuntur ab error amet quos excepturi voluptatum nesciunt accusamus eum quidem."
        },
        {
          title: "Artificial Intelligence",
          person: "Steve Rogers",
          due: "2019-10-12",
          status: "overdue",
          content:
            "Lorem ipsum dolor sit, amet consectetur adipisicing elit. Repudiandae rerum, delectus ullam molestias dicta eos minus laborum consequuntur? Dolor consequuntur ab error amet quos excepturi voluptatum nesciunt accusamus eum quidem."
        }
      ]
    };
  },

  computed: {
    myProjects() {
      return this.projects.filter(project => {
        return project.person === 'Sunny Kumar';
      })
    }
  }
};
</script>
