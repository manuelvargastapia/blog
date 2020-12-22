<template>
  <v-container>
    <v-card v-for="article of articles" :key="article">
      <nuxt-link :to="article.dir">
        <v-img
          v-if="article.featured"
          :src="require(`static/featured_images/${article.featured}`)"
          :alt="article.title"
        ></v-img>
        <h3>{{ article.title }}</h3>
        <p>{{ article.description }}</p>
      </nuxt-link>
    </v-card>
  </v-container>
</template>

<script>
export default {
  async asyncData({ $content }) {
    const articles = await $content({ deep: true })
      .only(['title', 'description', 'slug', 'dir', 'featured'])
      .sortBy('createdAt', 'desc')
      .fetch()
    return { articles }
  },
}
</script>
