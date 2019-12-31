<template>
  <div>
    <v-card class="mx-1" outlined min-width="150" max-width="300" v-on:click="show=!show">
      <v-card-title
        ><div class="text-truncate">
          {{ title }}
        </div></v-card-title
      >
    </v-card>
    <v-dialog
        v-model="show"
        width=500
      >
    <v-card class="mx-auto markdown-area" v-on:click="show=!show">
      <v-card-title primary-title class="headline grey lighten-2"
        ><div class="text-truncate">
          {{ title }}
        </div></v-card-title
      >
      <v-card-text class="pt-6">
        <vue-markdown :source="content"></vue-markdown
      ></v-card-text>
    </v-card>
    </v-dialog>
  </div>
</template>

<script lang="ts">
import Vue from 'vue'
import VueMarkdown from 'vue-markdown'

export default Vue.extend({
  name: 'todo-item',
  props: ['memo'],
  data: function () {
    return {
      show: !!this.memo.created
    }
  },
  components: {
    VueMarkdown
  },
  methods: {
  },
  computed: {
    title: function () {
      return this.memo.title
    },
    content: function () {
      return this.memo.content
    }
  }
})
</script>
