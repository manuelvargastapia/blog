<template>
  <div>
    <v-card class="mx auto" max-width="1080" max-height="500" elevation="0">
    </v-card>
    <v-responsive max-width="1080">
      <div class="pa-3 secondary rounded-xl">
        <v-img
          v-if="app.featured"
          :src="require(`static/featured_images/${app.featured}`)"
          :alt="app.name"
          class="rounded-image"
          min-width="100"
          contain
        ></v-img>
      </div>
      <v-container fluid>
        <v-card-title class="headline" v-text="app.name"> </v-card-title>
        <v-card-subtitle v-text="app.preview"> </v-card-subtitle>
        <v-row>
          <v-col align="center">
            <v-btn v-if="app.repo" :href="app.repo" target="_blank" text>
              <v-card-text>Repositorio</v-card-text>
            </v-btn>
            <v-btn
              v-if="app.download"
              :href="app.download"
              target="_blank"
              text
            >
              <v-card-text>Descarga</v-card-text>
            </v-btn>
            <nuxt-link v-if="app.article_slug" :to="app.article_slug">
              <v-btn text>
                <v-card-text>Artículo</v-card-text>
              </v-btn>
            </nuxt-link>
            <v-btn
              v-if="app.reference"
              :href="app.reference"
              target="_blank"
              text
            >
              <v-card-text>Referencia</v-card-text>
            </v-btn>
          </v-col>
        </v-row>
        <v-card-actions>
          <v-card-action>
            <v-btn icon>
              <v-icon>mdi-heart-outline</v-icon>
            </v-btn>
          </v-card-action>
          <v-card-action>
            <v-btn icon>
              <v-icon>mdi-comment-outline</v-icon>
            </v-btn>
          </v-card-action>
          <v-card-action>
            <v-btn icon>
              <v-icon>mdi-share-variant-outline</v-icon>
            </v-btn>
          </v-card-action>
        </v-card-actions>
      </v-container>
    </v-responsive>
  </div>
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
