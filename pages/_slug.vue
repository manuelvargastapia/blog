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
  async asyncData({ params, error }) {
    const pageTable = await getPageTable(
      '1c810a1cdb3a497f83e4bdc779e2377e',
      'https://notion-cloudflare-worker.manuelvargastapia.workers.dev/v1'
    )
    const page = pageTable.find(
      (item) => item.published && item.slug === params.slug
    )
    const blockMap = await getPageBlocks(
      page.id,
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
