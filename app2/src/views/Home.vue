<template>
  <v-container fluid class="grey lighten-4 fill-height">
    <v-row justify="center" align="center">
      <v-col class="shrink">
        <v-tooltip right>
          <template v-slot:activator="{ on }">
            <v-btn :href="source" icon large target="_blank" v-on="on">
              <v-icon large>mdi-code-tags</v-icon>
            </v-btn>
          </template>
          <span>Source</span>
        </v-tooltip>
        <v-tooltip right>
          <template v-slot:activator="{ on }">
            <v-btn
              icon
              large
              href="https://codepen.io/johnjleider/pen/zgxbYO"
              target="_blank"
              v-on="on"
            >
              <v-icon large>mdi-codepen</v-icon>
            </v-btn>
          </template>
          <span>Codepen</span>
        </v-tooltip>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
export default {
  props: {
    source: String
  }
}
</script>
