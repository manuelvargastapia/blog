<template>
  <NotionRenderer
    :block-map="blockMap"
    :page-link-options="pageLinkOptions"
    full-page
    prism
  />
</template>

<script>
import { NotionRenderer, getPageBlocks, getPageTable } from 'vue-notion'
import 'prismjs'
import 'prismjs/themes/prism.css'

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
      page.source[0],
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
</style>
