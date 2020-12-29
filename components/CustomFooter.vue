<template>
  <div>
    <div class="d-none d-sm-block mt-16">
      <v-footer app padless absolute color="transparent">
        <v-card
          flat
          tile
          width="100%"
          class="lighten-1 text-center d-flex"
          color="transparent"
        >
          <v-card-text>
            <strong>{{ new Date().getFullYear() }} © Manuel Vargas</strong>
          </v-card-text>
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
            <strong>Contáctame</strong>
            <strong>Privacidad y Términos de uso</strong>
          </v-card-text>
        </v-card>
      </v-footer>
    </div>
    <div class="d-sm-none">
      <v-footer app padless absolute color="transparent">
        <v-card
          flat
          tile
          width="100%"
          class="lighten-1 text-center"
          color="transparent"
        >
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
            <strong>Contáctame</strong>
          </v-card-text>
          <v-card-text>
            <strong>Privacidad y Términos de uso</strong>
          </v-card-text>
          <v-card-text>
            {{ new Date().getFullYear() }} — <strong>© Manuel Vargas</strong>
          </v-card-text>
        </v-card>
      </v-footer>
    </div>
  </div>
</template>

<script>
import {
  faGithubAlt,
  faLinkedinIn,
  faGoodreadsG,
  faInstagram,
} from '@fortawesome/free-brands-svg-icons'
import { faBars } from '@fortawesome/free-solid-svg-icons'
export default {
  data() {
    return {
      rrssIcons: [
        {
          icon: this.faGithubAlt,
          href: 'https://github.com/manuelvargastapia',
        },
        {
          icon: this.faGoodreadsG,
          href: 'https://www.goodreads.com/user/show/113995266-manuel',
        },
        {
          icon: this.faLinkedinIn,
          href: 'https://www.linkedin.com/in/manuel-vargas-tapia-6ba3351a5/',
        },
        {
          icon: this.faInstagram,
          href: 'https://www.instagram.com/manuelvargastapia/',
        },
      ],
    }
  },
  computed: {
    faGithubAlt() {
      return faGithubAlt
    },
    faLinkedinIn() {
      return faLinkedinIn
    },
    faGoodreadsG() {
      return faGoodreadsG
    },
    faInstagram() {
      return faInstagram
    },
    faBars() {
      return faBars
    },
  },
}
</script>
