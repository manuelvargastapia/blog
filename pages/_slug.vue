<template>
  <v-container fill-height fluid>
    <v-row justify="center" align="center">
      <v-col cols="auto">
        <v-img
          v-if="featured"
          :src="require(`static/featured_images/articles/${featured}`)"
          max-width="708px"
        ></v-img>
        <notion-renderer
          :block-map="blockMap"
          :page-link-options="pageLinkOptions"
          full-page
          prism
        />
      </v-col>
    </v-row>
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
      process.env.ARTICLES_TABLE,
      process.env.WORKER_URL
    )
    const page = pageTable.find(
      (item) => item.published && item.slug === params.slug
    )
    const blockMap = await getPageBlocks(page.id, process.env.WORKER_URL)
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
  font-family: -apple-system, Poppins, 'Segoe UI', Helvetica,
    'Apple Color Emoji', Arial, sans-serif, 'Segoe UI Emoji', 'Segoe UI Symbol' !important;
}
.v-application code {
  background: transparent !important;
  color: #dfc256;
  font-size: 90%;
}
.notion-title {
  text-align: left;
}
.notion-h1 {
  text-align: left;
}
.notion-h2 {
  text-align: left;
}
.notion-h3 {
  text-align: left;
}
.notion-hr {
  border-color: #3a3a3a4b !important;
}
</style>
