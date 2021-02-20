<template>
  <v-container>
    <v-row>
      <v-col align="center">
        <v-btn @click="reload">Reload</v-btn>
      </v-col>
    </v-row>
    <v-row v-if="!$fetchState.pending">
      <v-img :src="image.url" />
    </v-row>
  </v-container>
</template>

<script>
export default {
  data() {
    return {
      image: '',
    }
  },
  async fetch() {
    this.image = await this.$axios.$get(
      'https://www.nekos.life/api/v2/img//wallpaper'
    )
  },
  methods: {
    reload() {
      this.$fetch()
    },
  },
}
</script>
