<template>
  <articles-list :articles="articles"></articles-list>
</template>

<script>
import { getPageTable } from 'vue-notion'

export default {
  async asyncData() {
    const pageTable = await getPageTable(
      process.env.ARTICLES_TABLE,
      process.env.WORKER_URL
    )
    const articles = pageTable.filter((page) => page.published)
    return { articles }
  },
}
</script>
