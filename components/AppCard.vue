<template>
  <v-card class="mx-auto pa-4" max-width="800" elevation="0" color="#3a3a3a">
    <v-img
      v-if="app.featured"
      :src="require(`static/featured_images/apps/${app.featured}`)"
      :alt="app.name"
      class="rounded"
      contain
    />
    <v-container fluid>
      <v-card-title class="headline" v-text="app.name"> </v-card-title>
      <v-card-subtitle v-text="app.preview"> </v-card-subtitle>
      <v-row>
        <v-col align="start">
          <v-btn v-if="app.repo" :href="app.repo" target="_blank" text>
            <font-awesome-icon :icon="faGithub" size="2x" />
            <v-card-text>Repositorio</v-card-text>
          </v-btn>
          <nuxt-link v-if="app.article_slug" :to="app.article_slug">
            <v-btn text>
              <font-awesome-icon :icon="faBookOpen" size="2x" />
              <v-card-text>Artículo</v-card-text>
            </v-btn>
          </nuxt-link>
        </v-col>
      </v-row>
      <v-row>
        <v-col align="center">
          <a v-if="app.download_link" :href="app.download_link" target="_blank">
            <v-img
              v-if="app.download_badge"
              :src="app.download_badge"
              max-width="300"
              max-height="160"
              contain
            />
            <v-card-text v-else>Descarga</v-card-text>
          </a>
        </v-col>
      </v-row>
      <v-card-actions>
        <v-row justify="space-between" align="center">
          <div>
            <v-btn icon>
              <v-icon>mdi-heart-outline</v-icon>
            </v-btn>
            <v-btn icon>
              <v-icon>mdi-comment-outline</v-icon>
            </v-btn>
            <v-btn icon>
              <v-icon>mdi-share-variant-outline</v-icon>
            </v-btn>
          </div>
          <div>
            <v-card-text v-text="app.date" />
          </div>
        </v-row>
      </v-card-actions>
    </v-container>
  </v-card>
</template>

<script>
import { faGithub } from '@fortawesome/free-brands-svg-icons'
import { faBookOpen } from '@fortawesome/free-solid-svg-icons'
export default {
  props: {
    app: {
      type: [Object],
      required: true,
    },
  },
  data() {
    return { faGithub, faBookOpen }
  },
}
</script>

<style>
.v-application a:hover {
  text-decoration: none !important;
}
</style>
