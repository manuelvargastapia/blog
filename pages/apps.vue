<template>
  <apps-list :apps="apps"></apps-list>
</template>

<script>
import { getPageTable } from 'vue-notion'

export default {
  async asyncData() {
    const pageTable = await getPageTable(
      process.env.APPS_TABLE,
      process.env.WORKER_URL
    )
    const apps = pageTable.sort((a, b) => a.date - b.date)
    return { apps }
  },
}
</script>
