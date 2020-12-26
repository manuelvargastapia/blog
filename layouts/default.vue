<template>
  <v-app>
    <v-app-bar app flat>
      <v-toolbar-title>Manuel Vargas</v-toolbar-title>
      <v-spacer></v-spacer>
      <v-btn icon @click="$vuetify.theme.dark = !$vuetify.theme.dark">
        <v-icon>mdi-brightness-4</v-icon>
      </v-btn>
      <v-btn to="/" nuxt text> Blog </v-btn>
      <v-btn to="/apps" nuxt text> Apps </v-btn>
      <v-btn to="/about" nuxt text> Acerca de </v-btn>
    </v-app-bar>
    <!-- 
    MOBILE
    <v-navigation-drawer app>
    </v-navigation-drawer> -->
    <v-main>
      <v-container fluid>
        <nuxt />
      </v-container>
    </v-main>
    <v-footer app padless>
      <v-card flat tile width="100%" class="lighten-1 text-center d-flex">
        <v-card-text>
          {{ new Date().getFullYear() }} — <strong>© Manuel Vargas</strong>
        </v-card-text>
        <v-card-text>
          <v-btn icon>
            <font-awesome-icon :icon="faGithub" />
          </v-btn>
          <v-btn icon>
            <font-awesome-icon :icon="faLinkedin" />
          </v-btn>
          <v-btn icon>
            <font-awesome-icon :icon="faMedium" />
          </v-btn>
          <v-btn icon>
            <font-awesome-icon :icon="faInstagram" />
          </v-btn>
        </v-card-text>
        <v-card-text>
          <strong>Contáctame</strong>
          <strong>Privacidad y Términos de uso</strong>
        </v-card-text>
      </v-card>
    </v-footer>
  </v-app>
</template>

<script>
import {
  faGithub,
  faLinkedin,
  faMedium,
  faInstagram,
} from '@fortawesome/free-brands-svg-icons'

export default {
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
  },
}
</script>
