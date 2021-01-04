<template>
  <div class="mb-14">
    <v-card
      :class="{
        'd-flex': $vuetify.breakpoint.lg,
        'pa-4': $vuetify.breakpoint.mdAndDown,
        'px-4': $vuetify.breakpoint.lg,
      }"
      class="mx auto justify-space-between align-center"
      max-width="800"
      max-height="500"
      elevation="0"
    >
      <v-responsive :max-width="$vuetify.breakpoint.lg ? 400 : 800">
        <div class="pa-3 secondary rounded">
          <v-img
            v-if="article.featured"
            :src="require(`static/featured_images/${article.featured}`)"
            :alt="article.title"
            class="rounded"
            min-width="200"
            max-width="500"
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
