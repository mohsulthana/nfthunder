<template>
<div id="trait-rarity">
  <v-parallax height="100%" src="@/assets/wallpaper-gray.png" class="py-10">
    <v-row align="center" justify="center" class="text-center">
      <v-col class="d-flex justify-center" cols="12" sm="12">
        <v-img :max-width="maxWidth" src="https://static.wixstatic.com/media/1688f5_d380460293d544229d3dffdbe8cfac6e~mv2.png/v1/fill/w_791,h_1123,al_c,q_90,usm_0.66_1.00_0.01/NFThund%20-%20Trait.webp" lazy-src="https://static.wixstatic.com/media/1688f5_d380460293d544229d3dffdbe8cfac6e~mv2.png/v1/fill/w_791,h_1123,al_c,q_90,usm_0.66_1.00_0.01/NFThund%20-%20Trait.webp" />
      </v-col>
      <v-btn depressed large tile class="btn mb-10 mt-5 black--text" color="yellow accent-3">Rarity Chart</v-btn>
    </v-row>
    <v-row align="center" justify="center" class="text-center">
      <v-col class="d-flex justify-center" cols="12" sm="12">
        <v-img :max-width="maxWidth" src="@/assets/roadmap.webp" class="d-flex child-flex"></v-img>
      </v-col>
    </v-row>
  </v-parallax>
</div>
</template>

<script>
export default {
  name: 'trait',
  computed: {
    // eslint-disable-next-line vue/return-in-computed-property
    maxWidth () {
      switch (this.$vuetify.breakpoint.name) {
        case 'xs': return '100%'
        case 'sm' : return '100%'
        case 'lg': return '50%'
        case 'xl': return '50%'
      }
    }
  }
}
</script>
