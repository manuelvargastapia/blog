<template>
  <v-card class="mx auto" max-width="800" elevation="0">
    <v-responsive max-width="800">
      <div class="pa-3 secondary rounded-xl">
        <v-img
          v-if="app.featured"
          :src="require(`static/featured_images/${app.featured}`)"
          :alt="app.name"
          class="rounded-image"
          contain
        />
      </div>
      <v-container fluid>
        <v-card-title class="headline" v-text="app.name"> </v-card-title>
        <v-card-subtitle v-text="app.preview"> </v-card-subtitle>
        <v-row class="my-6">
          <v-col align="center">
            <v-btn
              v-if="app.download_link"
              :href="app.download_link"
              target="_blank"
              text
            >
              <v-img
                v-if="app.download_badge"
                :src="app.download_badge"
                max-width="300"
              />
              <v-card-text v-else>Descarga</v-card-text>
            </v-btn>
          </v-col>
        </v-row>
        <v-row>
          <v-col align="start">
            <v-btn v-if="app.repo" :href="app.repo" target="_blank" text>
              <v-card-text>Repositorio</v-card-text>
            </v-btn>
            <nuxt-link v-if="app.article_slug" :to="app.article_slug">
              <v-btn text>
                <v-card-text>Artículo</v-card-text>
              </v-btn>
            </nuxt-link>
          </v-col>
        </v-row>
        <v-card-actions>
          <v-btn icon>
            <v-icon>mdi-heart-outline</v-icon>
          </v-btn>
          <v-btn icon>
            <v-icon>mdi-comment-outline</v-icon>
          </v-btn>
          <v-btn icon>
            <v-icon>mdi-share-variant-outline</v-icon>
          </v-btn>
        </v-card-actions>
      </v-container>
    </v-responsive>
  </v-card>
</template>

<script>
export default {
  props: {
    app: {
      type: [Object],
      required: true,
    },
  },
}
</script>
