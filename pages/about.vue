<template>
  <v-container fill-height fluid>
    <v-row justify="center" align="center">
      <v-col
        style="align-items: center"
        class="d-flex flex-column align-items-center"
        cols="auto"
      >
        <v-img
          v-if="featured"
          :src="require(`static/featured_images/about/${featured}`)"
          width="250"
          height="250"
        />
        <v-col>
          <v-btn
            v-for="(item, index) in rrssIcons"
            :key="index"
            :href="item.href"
            icon
            target="_blank"
            class="mx-2 mt-10 pa-6"
          >
            <font-awesome-icon :icon="item.icon" size="2x" />
          </v-btn>
        </v-col>
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
import {
  faGithubAlt,
  faRedditAlien,
  faGoodreadsG,
} from '@fortawesome/free-brands-svg-icons'
import { faEnvelope } from '@fortawesome/free-solid-svg-icons'

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
      rrssIcons: [
        {
          icon: faGithubAlt,
          href: 'https://github.com/manuelvargastapia',
        },
        {
          icon: faGoodreadsG,
          href: 'https://www.goodreads.com/user/show/113995266-manuel',
        },
        {
          icon: faRedditAlien,
          href: 'https://www.reddit.com/user/Sea_Inflation_7446',
        },
        {
          icon: faEnvelope,
          href: 'mailto:contacto@manuelvargas.dev',
        },
      ],
      navItems: [
        { title: 'Blog', to: '/' },
        { title: 'Apps', to: 'apps' },
        { title: 'Acerca de', to: 'about' },
      ],
    }
  },
}
</script>

<style>
@import 'vue-notion/src/styles.css';

.notion {
  color: rgb(255, 255, 255);
}
.notion-title {
  text-align: left;
}
.notion-h2 {
  text-align: left;
}
.notion-hr {
  margin: 6px 0px;
  padding: 0;
  border-top-width: 1px;
  border-bottom-width: 0;
  border-color: #3a3a3a4b !important;
}
</style>
