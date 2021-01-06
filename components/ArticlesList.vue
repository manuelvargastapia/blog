<template>
  <v-container fill-height>
    <v-row justify="center" align="center">
      <v-col cols="auto">
        <most-recent-article-card
          :article="articles[0]"
        ></most-recent-article-card>
      </v-col>
      <v-row>
        <v-col
          v-for="article in articles.slice(1)"
          :key="article.title"
          :cols="$vuetify.breakpoint.mdAndUp ? 6 : `auto`"
        >
          <next-article-card :article="article"></next-article-card>
        </v-col>
      </v-row>
    </v-row>
  </v-container>
</template>

<script>
export default {
  props: {
    articles: {
      type: [Array],
      required: true,
    },
  },
}
</script>
