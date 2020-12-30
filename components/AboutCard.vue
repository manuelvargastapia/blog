<template>
  <v-card class="mx auto" max-width="800" elevation="0">
    <v-card-title>{{ aboutInfo.title }}</v-card-title>
    <v-card-text>{{ aboutInfo.content }}</v-card-text>
  </v-card>
</template>

<script>
export default {
  props: {
    aboutInfo: {
      type: [Object],
      required: true,
    },
  },
}
</script>
