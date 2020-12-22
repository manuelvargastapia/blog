<template>
  <last-article-card :articles="articles" />
</template>

<script>
import LastArticleCard from '~/components/LastArticleCard.vue'
export default {
  components: { LastArticleCard },
  async asyncData({ $content }) {
    const articles = await $content({ deep: true })
      .only(['title', 'description', 'slug', 'dir', 'featured'])
      .sortBy('createdAt', 'desc')
      .fetch()
    return { articles }
  },
}
</script>
