<template>
  <div class="mb-14">
    <v-card class="mx auto" max-width="1080" max-height="500" elevation="0">
    </v-card>
    <div
      :class="{ 'd-flex': $vuetify.breakpoint.lg }"
      class="flex-no-wrap justify-space-between"
    >
      <v-responsive max-width="600">
        <div class="pa-6 secondary rounded-xl">
          <v-img
            v-if="article.featured"
            :src="require(`static/featured_images/${article.featured}`)"
            :alt="article.title"
            class="rounded-image"
            min-width="200"
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

<style>
.rounded-image {
  border-radius: 16px;
}
</style>
