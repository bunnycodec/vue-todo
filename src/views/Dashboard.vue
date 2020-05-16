<template>
  <div class="dashboard px-4">
    <h1 class="py-4 title grey--text text--darken-1">DASHBOARD</h1>

    <v-container class="py-12">
      <v-row class="mb-5 pa-3">
        <v-tooltip top v-for="value in sortButtons" :key="value.click">
          <template v-slot:activator="{ on }">
            <v-btn v-on="on" class="ml-3 grey accent-1" @click="sortBy(value.click)">
              <v-icon left>{{value.icon}}</v-icon>
              <span class="caption text-capitalize">{{value.title}}</span>
            </v-btn>
          </template>
          <span>{{value.tooltip}}</span>
        </v-tooltip>
      </v-row>

      <v-card
        :class="`mb-1 project ${project.status}`"
        flat
        v-for="project in projects"
        :key="project.title"
      >
        <v-row class="pa-3">
          <v-col cols="12" sm="12" md="6">
            <div class="caption grey--text text--darken-3">Project Title</div>
            <div class="black--text">{{project.title}}</div>
          </v-col>
          <v-col cols="6" sm="4" md="2">
            <div class="caption grey--text text--darken-3">Person</div>
            <div class="black--text">{{project.person}}</div>
          </v-col>
          <v-col cols="6" sm="4" md="2">
            <div class="caption grey--text text--darken-3">Due by</div>
            <div class="black--text">{{dueDate(project.due)}}</div>
          </v-col>
          <v-col cols="6" sm="4" md="2">
            <div class="float-right">
              <v-chip
                small
                :color="changeColor(project.status)"
                class="white--text my-2 caption text-uppercase"
              >{{project.status}}</v-chip>
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
      sortButtons: [
        {
          icon: "mdi-folder",
          title: "title",
          click: "title",
          tooltip: "Sort by Project Name"
        },
        {
          icon: "mdi-account",
          title: "person",
          click: "person",
          tooltip: "Sort by Person Name"
        },
        {
          icon: "mdi-calendar",
          title: "date",
          click: "due",
          tooltip: "Sort by Due Date"
        },
        {
          icon: "mdi-account-details",
          title: "status",
          click: "status",
          tooltip: "Sort by Status"
        }
      ],
      months: [
        "Jan",
        "Feb",
        "Mar",
        "Apr",
        "May",
        "Jun",
        "Jul",
        "Aug",
        "Sep",
        "Oct",
        "Nov",
        "Dec"
      ],
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
  methods: {
    changeColor(value) {
      if (value === "ongoing") return "amber darken-1";
      else if (value === "complete") return "green";
      else return "red";
    },

    sortBy(value) {
      this.projects.sort((a, b) => (a[value] < b[value] ? -1 : 1));
    },

    dueDate(val) {
      let arr = val.split("-");
      let ans = "";
      let temp = parseInt(arr[2], 10);
      if ((temp > 3 && temp < 21) || (temp > 23 && temp < 31))
        ans = temp + "th ";
      else if (temp == 1 || temp == 21 || temp == 31) ans = temp + "st ";
      else if (temp == 2 || temp == 22) ans = temp + "nd ";
      else ans = temp + "rd ";
      ans += this.months[parseInt(arr[1], 10)] + " " + arr[0];
      return ans;
    }
  }
};
</script>

<style lang="scss">
@mixin dashboard-bkg-col {
  background-color: #bdbdbd;
}

.dashboard .project.ongoing {
  border-left: 0.5rem solid #ffb300;
  @include dashboard-bkg-col();
}
.dashboard .project.complete {
  @include dashboard-bkg-col();
  border-left: 0.5rem solid #458868;
}
.dashboard .project.overdue {
  @include dashboard-bkg-col();
  border-left: 0.5rem solid #bb0a21;
}
</style>
