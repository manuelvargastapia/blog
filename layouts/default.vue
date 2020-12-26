<template>
  <v-app>
    <v-app-bar app flat absolute color="transparent">
      <v-toolbar-title>Manuel Vargas</v-toolbar-title>
      <v-spacer></v-spacer>
      <div class="d-none d-md-block">
        <v-container v-for="align in alignments" :key="align">
          <v-row align="center">
            <v-btn icon @click="$vuetify.theme.dark = !$vuetify.theme.dark">
              <v-icon>mdi-brightness-4</v-icon>
            </v-btn>
            <v-col v-for="(item, index) in navItems" :key="index">
              <v-btn :to="item.to" nuxt text>
                {{ item.title }}
              </v-btn>
            </v-col>
          </v-row>
        </v-container>
      </div>
      <div class="d-md-none">
        <v-menu offset-y>
          <template v-slot:activator="{ on, attrs }">
            <v-btn icon v-bind="attrs" v-on="on">
              <font-awesome-icon :icon="faBars" />
            </v-btn>
          </template>
          <v-list>
            <v-list-item>
              <v-btn icon @click="$vuetify.theme.dark = !$vuetify.theme.dark">
                <v-icon>mdi-brightness-4</v-icon>
              </v-btn>
            </v-list-item>
            <v-list-item v-for="(item, index) in navItems" :key="index">
              <v-list-item-title
                ><v-btn :to="item.to" nuxt text>
                  {{ item.title }}
                </v-btn></v-list-item-title
              >
            </v-list-item>
          </v-list>
        </v-menu>
      </div>
    </v-app-bar>
    <v-main>
      <v-container fluid>
        <nuxt />
      </v-container>
    </v-main>
    <v-footer app padless absolute color="transparent">
      <v-card
        flat
        tile
        width="100%"
        class="lighten-1 text-center d-flex"
        color="transparent"
      >
        <v-card-text>
          {{ new Date().getFullYear() }} — <strong>© Manuel Vargas</strong>
        </v-card-text>
        <v-card-text>
          <v-btn
            icon
            href="https://github.com/manuelvargastapia"
            target="_blank"
          >
            <font-awesome-icon :icon="faGithub" />
          </v-btn>
          <v-btn
            icon
            href="https://www.linkedin.com/in/manuel-vargas-tapia-6ba3351a5/"
            target="_blank"
          >
            <font-awesome-icon :icon="faLinkedin" />
          </v-btn>
          <v-btn icon href="https://medium.com/@manueldev" target="_blank">
            <font-awesome-icon :icon="faMedium" />
          </v-btn>
          <v-btn
            icon
            href="https://www.instagram.com/manuelvargastapia/"
            target="_blank"
          >
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
import { faBars } from '@fortawesome/free-solid-svg-icons'

export default {
  data() {
    return {
      navItems: [
        { title: 'Blog', to: '/' },
        { title: 'Apps', to: 'apps' },
        { title: 'Acerca de', to: 'about' },
      ],
      alignments: ['center'],
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
