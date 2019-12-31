<template>
  <v-app id="keep" >
    <v-app-bar app clipped-left color="amber">
      <v-app-bar-nav-icon @click="drawer = !drawer" />
      <span class="title ml-3 mr-5"
        >My <span class="font-weight-light">Page</span></span
      >
      <v-text-field
        solo-inverted
        flat
        hide-details
        label="Search"
        prepend-inner-icon="search"
      />

      <v-spacer />
    </v-app-bar>

    <v-navigation-drawer v-model="drawer" app clipped color="grey lighten-4">
      <v-list dense class="grey lighten-4">
        <template v-for="(item, i) in items">
          <v-row v-if="item.heading" :key="i" align="center">
            <v-col cols="5">
              <v-subheader v-if="item.heading">
                {{ item.heading }}
              </v-subheader>
            </v-col>
          </v-row>
          <v-divider v-else-if="item.divider" :key="i" dark class="my-4" />
          <v-list-item v-else :key="i" link v-on:click="route(item.link)">
            <v-list-item-action>
              <v-icon>{{ item.icon }}</v-icon>
            </v-list-item-action>
            <v-list-item-content>
              <v-list-item-title class="grey--text">
                {{ item.text }}
              </v-list-item-title>
            </v-list-item-content>
          </v-list-item>
        </template>
      </v-list>
    </v-navigation-drawer>

    <v-content>
      <router-view />
    </v-content>
  </v-app>
</template>

<script>
export default {
  name: 'App',
  data: () => ({
    drawer: null,
    items: [
      { icon: 'home', text: 'Home', link: '/' },
      { divider: true },
      { heading: 'TODO-LIST' },
      { icon: 'add', text: 'Create new todo-list', link: '/todo' },
      { divider: true },
      { icon: 'settings', text: 'Settings' }
    ]
  }),
  methods: {
    route: function (link) {
      this.$router.push(link)
    }
  }
}
</script>

<style>
#keep .v-navigation-drawer__border {
  display: none;
}
</style>
