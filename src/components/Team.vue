<template>
<div id="team" class="grey darken-2 py-5">
  <v-container>
    <v-row>
      <v-col>
        <h1 class="display-4 text-center font-weight-bold white--text">Team</h1>
      </v-col>
    </v-row>
    <v-row align="center" justify="center" class="text-center">
      <v-col cols="3" @click="openPage('https://twitter.com/nfthund')">
        <div class="d-flex justify-center align-center">
          <v-img src="@/assets/Sticker Grey.png" lazy-src="@/assets/Sticker Grey.png" aspect-ratio="1" max-height="98" max-width="101" />
        </div>
        <h3 class="white--text text-center">@NFThund</h3>
        <h4 class="white--text text-center">Motivation Artist</h4>
      </v-col>
      <v-col cols="3" @click="openPage('https://twitter.com/rmondc')">
        <div class="d-flex justify-center align-center">
          <v-img class="d-flex child-flex justify-center" src="@/assets/Sticker cyan.png" lazy-src="@/assets/Sticker cyan.png" aspect-ratio="1" max-height="98" max-width="101" />
        </div>
        <h3 class="white--text text-center">@rmondc</h3>
        <h4 class="white--text text-center">Creative Mind</h4>
      </v-col>
      <v-col cols="3">
        <div class="d-flex justify-center align-center">
          <v-img src="@/assets/Sticker Magenta.png" lazy-src="@/assets/Sticker Magenta.png" aspect-ratio="1" max-height="98" max-width="101" />
        </div>
        <h3 class="white--text text-center">@Vacant</h3>
        <h4 class="white--text text-center">Positive Enthusiasm</h4>
      </v-col>
      <v-col cols="3">
        <div class="d-flex justify-center align-center">
          <v-img src="@/assets/Sticker Yellow.png" lazy-src="@/assets/Sticker Yellow.png" aspect-ratio="1" max-height="98" max-width="101" />
        </div>
        <h3 class="white--text text-center">@Vacant</h3>
        <h4 class="white--text text-center">Artistic Techie</h4>
      </v-col>
    </v-row>
  </v-container>
</div>
</template>

<script>
export default {
  name: 'team',
  methods: {
    openPage (link) {
      window.open(link)
    }
  }
}
</script>

<style>
#team  .v-image {
  cursor: pointer;
}
</style>