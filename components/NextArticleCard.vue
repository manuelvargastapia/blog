<template>
  <v-card
    :class="{
      'd-flex': $vuetify.breakpoint.lgAndUp,
      'py-4': $vuetify.breakpoint.mdAndDown,
    }"
    class="mx-auto justify-space-between align-center pa-4"
    max-width="600"
    elevation="0"
    color="#3a3a3a"
  >
    <v-responsive :max-width="$vuetify.breakpoint.lgAndUp ? 250 : 600">
      <v-img
        v-if="article.featured"
        :src="require(`static/featured_images/articles/${article.featured}`)"
        :alt="article.title"
        class="rounded"
        min-width="200"
        max-height="220"
        cover
      ></v-img>
    </v-responsive>
    <v-container fluid class="d-flex flex-column justify-center">
      <nuxt-link :to="article.slug">
        <v-card-title class="headline-3" v-text="article.title" />
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
</template>

<script>
export default {
  props: {
    article: {
      type: [Object],
      required: true,
    },
  },
  computed: {
    maxWidth() {
      switch (this.$vuetify.breakpoint.name) {
        case 'xs':
        case 'sm':
        case 'md':
          return 400
        case 'lg':
        case 'xl':
          return 300
        default:
          return 400
      }
    },
  },
}
</script>

<style>
.v-card__title {
  word-break: normal;
}
.v-responsive__content {
  height: 220px;
  width: 400px;
}
</style>
