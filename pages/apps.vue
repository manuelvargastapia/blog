<template>
  <apps-list :apps="apps"></apps-list>
</template>

<script>
import { getPageTable } from 'vue-notion'

export default {
  async asyncData() {
    const pageTable = await getPageTable(
      'f00b832ddd3b4399ad38d01e4a1788e7',
      'https://notion-cloudflare-worker.manuelvargastapia.workers.dev/v1'
    )
    const apps = pageTable.sort((a, b) => a.date - b.date)
    return { apps }
  },
}
</script>
