<template>
  <v-container fill-height class="text-justify">
    <v-row justify="center" align="center">
      <v-col cols="auto">
        <v-img
          v-if="featured"
          :src="require(`static/featured_images/${featured}`)"
          width="200"
          height="200"
        />
      </v-col>
    </v-row>
    <v-row justify="center" align="center">
      <v-col cols="auto">
        <notion-renderer
          :block-map="blockMap"
          :page-link-options="pageLinkOptions"
          full-page
        />
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
import { NotionRenderer, getPageBlocks, getPageTable } from 'vue-notion'

export default {
  components: { NotionRenderer },
  async asyncData({ error }) {
    const pageTable = await getPageTable(
      '0940a94496fc4adfbb0c73af221ab8b7',
      'https://notion-cloudflare-worker.manuelvargastapia.workers.dev/v1'
    )
    const blockMap = await getPageBlocks(
      pageTable[0].id,
      'https://notion-cloudflare-worker.manuelvargastapia.workers.dev/v1'
    )
    if (!blockMap || blockMap.error) {
      return error({ statusCode: 404, message: 'Post not found' })
    }
    return { blockMap, featured: pageTable[0].featured }
  },
  data() {
    return {
      pageLinkOptions: { components: 'NuxtLink', href: 'to' },
    }
  },
}
</script>

<style>
@import 'vue-notion/src/styles.css';

.notion {
  color: rgb(255, 255, 255);
}
</style>
