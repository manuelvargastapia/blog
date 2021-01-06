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
          <v-card-text
            style="text-align: start"
            v-text="`© ${new Date().getFullYear()} Manuel Vargas`"
          />
          <v-card-text>
            <v-btn
              v-for="(item, index) in rrssIcons"
              :key="index"
              :href="item.href"
              icon
              target="_blank"
              class="mx-3"
            >
              <font-awesome-icon :icon="item.icon" size="2x" />
            </v-btn>
          </v-card-text>
          <v-card-text style="text-align: end">
            <v-btn
              class="body-2"
              href="mailto:manuelvargastapia@gmail.com"
              target="_blank"
              text
            >
              Contáctame
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
              class="mx-3"
            >
              <font-awesome-icon :icon="item.icon" size="2x" />
            </v-btn>
          </v-card-text>
          <v-card-text>
            <v-btn
              class="body-2"
              href="mailto:manuelvargastapia@gmail.com"
              target="_blank"
              text
            >
              Contáctame
            </v-btn>
          </v-card-text>
          <v-card-text v-text="`© ${new Date().getFullYear()} Manuel Vargas`" />
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
