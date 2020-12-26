<template>
  <articles-list :articles="articles"></articles-list>
</template>

<script>
import { getPageTable } from 'vue-notion'
import ArticlesList from '../components/ArticlesList'

export default {
  components: { ArticlesList },
  async asyncData() {
    const pageTable = await getPageTable(
      '1c810a1cdb3a497f83e4bdc779e2377e',
      'https://notion-cloudflare-worker.manuelvargastapia.workers.dev/v1'
    )
    const articles = pageTable
      .filter((page) => page.published)
      .sort((a, b) => a.date - b.date)
    return { articles }
  },
}
</script>
