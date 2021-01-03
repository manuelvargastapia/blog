<template>
  <div class="mb-14">
    <v-card
      :class="{ 'd-flex': $vuetify.breakpoint.lg }"
      class="mx auto justify-space-between align-center px-4"
      max-width="800"
      max-height="400"
      elevation="0"
    >
      <v-responsive max-width="400">
        <div class="pa-3 secondary rounded-xl">
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
          <v-card-title class="headline" v-text="article.title" />
        </nuxt-link>
        <v-card-subtitle v-text="article.preview" />
        <v-card-actions class="pr-md-3 pl-sm-6">
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
              <v-card-text v-text="article.date" />
            </div>
          </v-row>
        </v-card-actions>
      </v-container>
    </v-card>
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
