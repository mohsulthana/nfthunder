<template>
<div id="team">
  <div class="grey darken-2 py-5">
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
  <v-container>
    <v-row align="center" justify="center">
      <v-col class="d-none d-md-flex d-md-none justify-center">
        <v-img src="@/assets/twitter.png" @click="openPage('https://twitter.com/nfthund')" class="mt-7" max-height="48" max-width="48"></v-img>
        <v-img src="@/assets/discord.png" @click="openPage('https://discord.com/invite/NKsuXaENbX')" class="mt-7" max-height="48" max-width="48"></v-img>
        <v-img src="@/assets/pentas.png" @click="openPage('https://app.pentas.io/user/nfthund')" class="mt-7" max-height="48" max-width="48"></v-img>
      </v-col>
    </v-row>
  </v-container>
</div>
</template>

<script>
export default {
  name: 'team',
  methods: {
    openPage(link) {
      window.open(link)
    }
  }
}
</script>

<style>
#team .v-image {
  cursor: pointer;
}
</style>
