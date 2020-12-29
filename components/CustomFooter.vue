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
            >
              <font-awesome-icon :icon="item.icon" />
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
            >
              <font-awesome-icon :icon="item.icon" />
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
  faGithub,
  faLinkedin,
  faMedium,
  faInstagram,
} from '@fortawesome/free-brands-svg-icons'
import { faBars } from '@fortawesome/free-solid-svg-icons'
export default {
  data() {
    return {
      rrssIcons: [
        {
          icon: this.faGithub,
          href: 'https://github.com/manuelvargastapia',
        },
        {
          icon: this.faLinkedin,
          href: 'https://www.linkedin.com/in/manuel-vargas-tapia-6ba3351a5/',
        },
        {
          icon: this.faMedium,
          href: 'https://medium.com/@manueldev',
        },
        {
          icon: this.faInstagram,
          href: 'https://www.instagram.com/manuelvargastapia/',
        },
      ],
    }
  },
  computed: {
    faGithub() {
      return faGithub
    },
    faLinkedin() {
      return faLinkedin
    },
    faMedium() {
      return faMedium
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
