<template>
  <notion-renderer
    :block-map="blockMap"
    :page-link-options="pageLinkOptions"
    full-page
  />
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
    return { blockMap }
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
