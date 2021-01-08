<template>
  <v-container fluid>
    <v-parallax
      v-if="featured"
      :src="require(`static/featured_images/articles/${featured}`)"
      height="300"
      width="100%"
    ></v-parallax>
    <notion-renderer
      :block-map="blockMap"
      :page-link-options="pageLinkOptions"
      full-page
      prism
    />
  </v-container>
</template>

<script>
import { NotionRenderer, getPageBlocks, getPageTable } from 'vue-notion'
import 'prismjs'
import 'prismjs/themes/prism-okaidia.css'
import 'prismjs/components/prism-bash'
import 'prismjs/components/prism-json'
import 'prismjs/components/prism-dart'

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
    return { blockMap, featured: page.featured }
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
.v-application code {
  background: transparent;
  font-size: 90%;
}
.notion-title {
  text-align: left;
}
.notion-h2 {
  text-align: left;
}

.container {
  padding: 0;
}
</style>
