<template>
  <div>
    <div class="d-none d-sm-block mt-16">
      <v-footer app padless absolute color="transparent">
        <v-card
          flat
          tile
          width="100%"
          class="text-center d-flex align-center"
          color="transparent"
        >
          <v-card-text>
            <v-btn
              v-for="(item, index) in rrssIcons"
              :key="index"
              :href="item.href"
              icon
              target="_blank"
              class="mx-2 pa-6"
            >
              <font-awesome-icon :icon="item.icon" size="2x" />
            </v-btn>
          </v-card-text>
        </v-card>
      </v-footer>
    </div>
    <div class="d-sm-none">
      <v-footer app padless absolute color="transparent">
        <v-card flat tile width="100%" class="text-center" color="transparent">
          <v-card-text>
            <v-btn
              v-for="(item, index) in rrssIcons"
              :key="index"
              :href="item.href"
              icon
              target="_blank"
              class="mx-2 pa-6"
            >
              <font-awesome-icon :icon="item.icon" size="2x" />
            </v-btn>
          </v-card-text>
        </v-card>
      </v-footer>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    rrssIcons: {
      type: [Array],
      required: true,
    },
  },
}
</script>
