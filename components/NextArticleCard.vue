<template>
  <div>
    <v-card class="mx auto" max-width="600" max-height="500" elevation="0">
    </v-card>
    <div
      :class="{ 'd-flex': $vuetify.breakpoint.lg }"
      class="flex-no-wrap justify-space-between"
    >
      <v-responsive max-width="400">
        <div class="pa-3 secondary rounded-xl d-none d-md-block">
          <v-img
            v-if="article.featured"
            :src="require(`static/featured_images/${article.featured}`)"
            :alt="article.title"
            class="rounded-image"
            min-width="100"
            contain
          ></v-img>
        </div>
      </v-responsive>
      <v-container fluid class="d-flex flex-column justify-center">
        <nuxt-link :to="article.slug">
          <v-card-title class="headline" v-text="article.title"> </v-card-title>
        </nuxt-link>
        <v-card-subtitle v-text="article.preview"> </v-card-subtitle>
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
    </div>
  </div>
</template>

<script>
export default {
  props: {
    article: {
      type: [Object],
      required: true,
    },
  },
}
</script>
