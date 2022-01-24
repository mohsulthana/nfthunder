<template>
<div id="roadmpad">
  <v-parallax src="@/assets/wallpaper.png">
    <v-row align="center" justify="center">
      <v-col class="text-center">
        <v-btn @click="openPage('https://app.pentas.io/user/nfthund')" depressed large tile class="text-center btn" color="purple accent-3">Buy on Pentas</v-btn>
      </v-col>
    </v-row>
  </v-parallax>
</div>
</template>

<script>
export default {
  name: 'Roadmap',
  methods: {
    openPage (link) {
      window.open(link)
    }
  }
}
</script>
