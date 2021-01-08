<template>
  <div class="mb-14">
    <v-card
      :class="{
        'd-flex': $vuetify.breakpoint.lgAndUp,
        'py-4': $vuetify.breakpoint.mdAndDown,
      }"
      class="mx-auto justify-space-between align-center px-4"
      max-width="800"
      elevation="0"
      color="#3a3a3a"
    >
      <v-responsive :max-width="$vuetify.breakpoint.lgAndUp ? 400 : 800">
        <v-img
          v-if="article.featured"
          :src="require(`static/featured_images/articles/${article.featured}`)"
          :alt="article.title"
          class="rounded"
          min-width="200"
          max-height="260"
          cover
        ></v-img>
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
.v-card__title {
  word-break: normal;
}
.v-responsive__content {
  height: 260px;
  width: 400px;
}
</style>
