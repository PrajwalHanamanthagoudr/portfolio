<template>
  <v-container>
    <v-app-bar app color="#131313" flat dark fixed style="position: fixed;">
      <v-app-bar-nav-icon class="nav" color="white" @click.stop="drawer = !drawer"></v-app-bar-nav-icon>
      <div class="logo  py-2 px-4 text-white">
        <h1><span style="color: #687EFF;">P</span>rajwal.</h1>
      </div>
      <v-spacer></v-spacer>
      <v-btn class="menu mr-3 text-white" @click="scroll(item.title)" text v-for="item in items" :key="item.title">
        {{ item.title }}
      </v-btn>
    </v-app-bar>
    <v-navigation-drawer color="black" v-model="drawer" app class="position-fixed" location="left">
      <v-list dense fixed>
        <center class="mt-16">
          <v-list-item v-for="item in items" :key="item.title" link :exact="item.exact" @click="scroll(item.title)">
            <v-list-item-icon>
              <v-icon>{{ item.icon }}</v-icon>
            </v-list-item-icon>
            <v-list-item-content>
              <v-list-item-title class="mb-4">{{ item.title }}</v-list-item-title>
            </v-list-item-content>
          </v-list-item>
        </center>
      </v-list>
    </v-navigation-drawer>
  </v-container>
</template>

<script>

export default {
  name: 'HelloWorld',

  data: () => ({
    drawer: false,
    items: [
      { title: 'Home', icon: 'mdi-home' },
      { title: 'About', icon: 'mdi-account' },
      { title: 'Services', icon: 'mdi-cogs' },
      { title: 'Portfolio', icon: 'mdi-briefcase' },
      { title: 'Contact', icon: 'mdi-phone' },

    ]
  }),
}
</script>

<style>
@media screen and (max-width: 600px) {
  .menu {
    visibility: hidden;
  }
}

@media screen and (min-width: 600px) {
  .nav {
    visibility: hidden;
  }
}
</style>
