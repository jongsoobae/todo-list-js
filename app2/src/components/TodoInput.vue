<template>
  <v-card flat v-bind:style="'background: inherit'">
    <v-text-field
      label="title"
      autofocus
      v-model="title"
    ></v-text-field>
    <v-textarea
      flat
      name="input-7-4"
      v-model="content"
      auto-grow
      clearable
      outlined
      label="content"
      v-on:focus="onFocusInput"
      v-on:blur="onBlurInput"
      rows=1
    ></v-textarea>
  </v-card>
</template>

<script lang="ts">
import Vue from 'vue'

export default Vue.extend({
  name: 'markdown-editor',
  data: () => ({
    title: '',
    content: ''
  }),
  methods: {
    onFocusInput: function (ev: any) {},
    onBlurInput: function (ev: any) {
      if (!this.title) {
        this.$el.querySelector('input[type=text]').focus()
        return
      }
      if (!this.content) {
        ev.target.focus()
        return
      }
      this.$emit('create-memo', this.title, this.content)
      this.initialize()
    },
    initialize: function () {
      this.title = ''
      this.content = ''
    }
  }
})
</script>
