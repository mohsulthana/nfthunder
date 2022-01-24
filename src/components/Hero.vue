<template>
<div id="hero">
  <v-img src="@/assets/main-vid.gif" height="850" aspect-ratio="2" alt="001 NFThunder GIF">
    <v-container class="py-10 mb-10">
      <v-row align="center" justify="center">
        <v-col>
          <v-row>
            <h1 class="text-h1 my-10 white--text pl-5" :class="{'text-h2': $vuetify.breakpoint.xs, 'text-h1': $vuetify.breakpoint.xl}">Motivation in a box.</h1>
            <h6 class="description font-weight-regular my-10 pl-5 white-text">The NFThunder is a collection of 999 unique thunders inspired by vintage collectible toys. They are minted on the Binance Smart Chain and comes with a motivational quote that serves as visual energy shots to your mind. The NFThunder is unique in its kind and comes with rarity analysis, They are highly tradeable but encouraged to be given as gifts to spread the motivation and positivity.</h6>
          </v-row>
          <v-row justify="center" align="center">
            <v-col>
              <v-btn depressed large tile class="my-10 ml-3" color="purple accent-3 btn" @click="goToPentas()">Buy on Pentas</v-btn>
            </v-col>
          </v-row>
        </v-col>
        <v-col class="text-center">
        </v-col>
      </v-row>
    </v-container>
  </v-img>
</div>
</template>

<script>
export default {
  name: 'hero',
  methods: {
    goToPentas() {
      window.open('https://app.pentas.io/user/nfthund')
    }
  }
}
</script>

<style scoped>
.title {
  font-size: 109px !important;
  line-height: 0.9em;
  color: white;
}

.description {
  font-size: 16px !important;
  letter-spacing: 0.01em !important;
  line-height: 1.3em !important;
  color: white;
}

.hero-image {
  background-image: url('https://static.wixstatic.com/media/1688f5_8b8578f526524a0f9a68771d64837fb1f000.jpg/v1/fill/w_980,h_800,al_c,q_85,usm_0.33_1.00_0.00/1688f5_8b8578f526524a0f9a68771d64837fb1f000.webp');
  background-size: cover;
  height: 80vh;
}
</style>
