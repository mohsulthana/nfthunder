<template>
<v-app>
  <v-app-bar app height="90">
    <v-app-bar-nav-icon @click="drawer = true" class="d-flex d-md-none"></v-app-bar-nav-icon>
    <v-container>
      <v-row>
        <div class="d-flex align-center">
          <v-img alt="NFThunder Logo" class="shrink mr-2" contain src="@/assets/logo.webp" transition="scale-transition" width="40%" height="104" />
        </div>

        <v-spacer></v-spacer>
        <div class="d-none d-md-flex d-md-none">
          <v-img src="@/assets/twitter.png" @click="openPage('https://twitter.com/nfthund')" class="mt-7" max-height="48" max-width="48"></v-img>
          <v-img src="@/assets/discord.png" @click="openPage('https://discord.com/invite/NKsuXaENbX')" class="mt-7" max-height="48" max-width="48"></v-img>
          <v-img src="@/assets/pentas.png" @click="openPage('https://app.pentas.io/user/nfthund')" class="mt-7" max-height="48" max-width="48"></v-img>
        </div>
      </v-row>
    </v-container>
  </v-app-bar>

  <v-navigation-drawer v-model="drawer" absolute bottom temporary>
    <v-list nav dense>
      <v-list-item-group v-model="group" active-class="deep-purple--text text--accent-4">
        <v-list-item>
          <v-list-item-title>Foo</v-list-item-title>
        </v-list-item>

        <v-list-item>
          <v-list-item-title>Bar</v-list-item-title>
        </v-list-item>

        <v-list-item>
          <v-list-item-title>Fizz</v-list-item-title>
        </v-list-item>

        <v-list-item>
          <v-list-item-title>Buzz</v-list-item-title>
        </v-list-item>
      </v-list-item-group>
    </v-list>
  </v-navigation-drawer>

  <v-main>
    <hero />
    <explore-product />
    <trait />
    <CTA />
    <Team />
  </v-main>

  <v-footer app absolute>
    <v-container fluid color="white">
      <v-row align="center" justify="center">
        <v-col>
          <h3 class="text-center"> &#169; {{ new Date().getFullYear() }} NFThunder</h3>
        </v-col>
      </v-row>
    </v-container>
  </v-footer>
</v-app>
</template>

<script>
import ExploreProduct from './components/ExploreProduct.vue';
import Hero from './components/Hero.vue';
import CTA from './components/CTA.vue';
import Trait from './components/Trait.vue';
import Team from './components/Team.vue';

export default {
  name: 'App',
  data() {
    return {
      drawer: false,
      group: null
    }
  },
  components: {
    CTA,
    ExploreProduct,
    Hero,
    Trait,
    Team
  },
  watch: {
      group () {
        this.drawer = false
      },
    },
  methods: {
    openPage(link) {
      window.open(link)
    }
  }
};
</script>

<style>
@font-face {
  font-family: "DIN";
  src: local("DIN"), url('./assets/fonts/DIN.ttf') format("truetype");
}
.v-application {
  font-family: "DIN" !important;
}
.btn {
  padding: 30px !important;
  color: white !important;
  width: fit-content;
}
</style>
