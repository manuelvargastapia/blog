<template>
  <div>
    <div>
      <h1>Mis Posts</h1>
      <div>
        <ul>
          <li v-for="(post, k) in posts" :key="k">
            <b>{{ post.date }}</b>
            <nuxt-link v-if="post.slug" :to="post.slug">
              <b>{{ post.title }}</b>
              {{ post.preview }}
            </nuxt-link>
          </li>
        </ul>
      </div>
      <div>
        <h2>Tags</h2>
        <ul>
          <li v-for="(tag, k) in tags" :key="k">
            <b>{{ tag }}</b>
            <ul>
              <li v-for="(post, k) in postsByTag.get(tag)" :key="k">
                <nuxt-link v-if="post.slug" :to="post.slug">
                  <b>{{ post.title }}</b>
                  {{ post.preview }}
                </nuxt-link>
              </li>
            </ul>
          </li>
        </ul>
      </div>
    </div>
  </div>
</template>

<script>
import { getPageTable } from 'vue-notion'

export default {
  async asyncData() {
    const pageTable = await getPageTable(
      '1c810a1cdb3a497f83e4bdc779e2377e',
      'https://notion-cloudflare-worker.manuelvargastapia.workers.dev/v1'
    )
    const posts = pageTable
      .filter((page) => page.published)
      .sort((a, b) => a.date - b.date)
    const postsByTag = pageTable
      .filter((page) => page.published)
      .reduce((map, currentPage) => {
        currentPage.tags.forEach((tag) =>
          map.has(tag)
            ? map.set(tag, [...map.get(tag), currentPage])
            : map.set(tag, [currentPage])
        )
        return map
      }, new Map())
    return {
      posts,
      postsByTag,
      tags: [...postsByTag.keys()].sort(),
    }
  },
}
</script>
