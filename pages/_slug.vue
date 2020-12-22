<template>
  <nuxt-content :document="article" />
</template>

<script>
export default {
  async asyncData({ $content, params }) {
    const articlePath = `/${params.slug}`
    const [article] = await $content({ deep: true })
      .where({ dir: articlePath })
      .fetch()
    return { article }
  },
}
</script>

<style></style>
