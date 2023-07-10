<template>
  <v-container>
    <v-app-bar app color="#131313" flat dark fixed style="position: fixed;">
      <div class="logo  py-2 px-4 text-white ml-10">
        <h1><span style="color: #687EFF;">Pr</span>ajwal.</h1>
      </div>
      <v-spacer></v-spacer>
      <v-app-bar-nav-icon class="nav mr-6" color="white" @click.stop="drawer = !drawer"></v-app-bar-nav-icon>
      <v-btn class="menu mr-3 text-white font-weight-bold" @click="scrollToSection(item.section)" text v-for="item in items"
        :key="item.title" :class="{ 'active': activePage === item.section }">
        {{ item.title }}
      </v-btn>
    </v-app-bar>
    <v-navigation-drawer color="black" v-model="drawer" app class="position-fixed" location="right">
      <v-list dense fixed>
        <center class="mt-16">
          <v-list-item v-for="item in items" :key="item.title" link :exact="item.exact"
            @click="scrollToSection(item.section)" :class="{ 'active': activePage === item.section }"
            :style="{ backgroundColor: activePage === item.section ? '#678EFF' : '',color: activePage === item.section ? 'black' : '' }">
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
    activePage: 'home',
    items: [
      { title: 'Home', icon: 'mdi-home', section: 'home' },
      { title: 'About', icon: 'mdi-account', section: 'about' },
      { title: 'Services', icon: 'mdi-cogs', section: 'services' },
      { title: 'Portfolio', icon: 'mdi-briefcase', section: 'portfolio' },
      { title: 'Contact', icon: 'mdi-phone', section: 'contact' },

    ]
  }),
  methods: {
    scrollToSection(section) {
      this.activePage = section;
      this.$emit('scrollToSection', section);
    }
  }
}
</script>

<style>
.active {
  text-decoration-line: underline;
  text-decoration-color: #678EFF;
  text-decoration-thickness: 3px; 
  text-underline-offset: 10px;
}

@media screen and (max-width: 800px) {
  .menu {
    display: none;
  }
}

@media screen and (min-width: 800px) {
  .nav {
    display: none;
  }
}
</style>
