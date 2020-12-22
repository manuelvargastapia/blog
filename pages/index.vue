<template>
  <v-col>
    <v-card v-for="article of articles" :key="article">
      <nuxt-link :to="{ name: 'slug', params: { slug: article.slug } }">
        <img :src="require(`assets/resources/${article.img}`)" alt="" />
        <h3>{{ article.title }}</h3>
        <p>{{ article.description }}</p>
      </nuxt-link>
    </v-card>
  </v-col>
</template>

<script>
export default {
  async asyncData({ $content, params }) {
    const articles = await $content('blog', params.slug)
      .only(['title', 'description', 'img', 'slug'])
      .sortBy('createdAt', 'asc')
      .fetch()

    return { articles }
  },
}
</script>
