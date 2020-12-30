<template>
  <v-container fill-height>
    <v-row justify="center" align="center">
      <v-col cols="auto">
        <about-card :about-info="aboutInfo"></about-card>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
import { getPageTable } from 'vue-notion'

export default {
  async asyncData() {
    const aboutInfo = await getPageTable(
      '0940a94496fc4adfbb0c73af221ab8b7',
      'https://notion-cloudflare-worker.manuelvargastapia.workers.dev/v1'
    )
    return { aboutInfo: aboutInfo[0] }
  },
}
</script>
