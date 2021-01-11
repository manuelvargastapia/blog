<template>
  <v-container fill-height>
    <v-row v-for="app in apps" :key="app.title" justify="center" align="center">
      <v-col cols="auto">
        <app-card :app="app"></app-card>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
export default {
  props: {
    apps: {
      type: [Array],
      required: true,
    },
  },
}
</script>
