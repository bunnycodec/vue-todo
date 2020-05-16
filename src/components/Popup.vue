<template>
  <v-dialog v-model="dialog" max-width="600">
    <template v-slot:activator="{ on }">
      <v-btn large flat color="success" v-on="on">
        <span class="font-weight-bold">Add New Project</span>
      </v-btn>
    </template>

    <v-card>
      <v-card-title class="headline grey lighten-2" primary-title
        >New Project</v-card-title
      >

      <v-card-text class="py-3">
        <v-form class="px-3" ref="form">
          <v-text-field
            v-model="title"
            prepend-icon="mdi-account"
            class="my-3"
            counter="10"
            outlined
            label="Title"
            :rules="textRules"
          ></v-text-field>
          <v-textarea
            v-model="content"
            prepend-icon="mdi-pencil"
            class="my-3"
            counter="300"
            outlined
            label="Information"
            :rules="textRules"
          ></v-textarea>

          <v-menu>
            <template v-slot:activator="{ on }">
              <v-text-field
                :value="dateFormatted"
                label="Due date"
                prepend-icon="mdi-calendar"
                v-on="on"
                :rules="textRules"
              ></v-text-field>
            </template>
            <v-date-picker flat dark color="teal" v-model="due"></v-date-picker>
          </v-menu>

          <v-btn class="mx-0 mb-3" color="success" flat @click="submitForm"
            >Add Project</v-btn
          >
          <v-btn
            class="float-right mb-3"
            color="amber darken-1"
            flat
            @click="clearForm"
            >Clear</v-btn
          >
        </v-form>
      </v-card-text>
    </v-card>
  </v-dialog>
</template>

<script>
import format from 'date-fns/format';
import parseISO from 'date-fns/parseISO';

export default {
  data() {
    return {
      title: '',
      content: '',
      due: null,
      textRules: [(v) => v.length >= 5 || 'Minimum Lenght Should be 5'],
    };
  },

  methods: {
    submitForm() {
      this.$refs.form.validate();
    },

    clearForm() {
      this.title = '';
      this.content = '';
      this.due = null;
      this.$refs.form.reset();
    },
  },

  computed: {
    dateFormatted() {
      return this.due ? format(parseISO(this.due), 'do MMM yyyy') : '';
    },
  },
};
</script>
