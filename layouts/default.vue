<template>
  <v-app>
    <custom-app-bar :nav-items="navItems" :fa-bars="faBars"></custom-app-bar>
    <v-main class="mb-16">
      <v-container fluid>
        <nuxt />
      </v-container>
    </v-main>
    <custom-footer :rrss-icons="rrssIcons"></custom-footer>
  </v-app>
</template>

<script>
import {
  faGithubAlt,
  faLinkedinIn,
  faGoodreadsG,
} from '@fortawesome/free-brands-svg-icons'
import { faBars, faEnvelope } from '@fortawesome/free-solid-svg-icons'
export default {
  data() {
    return {
      rrssIcons: [
        {
          icon: faGithubAlt,
          href: 'https://github.com/manuelvargastapia',
        },
        {
          icon: faGoodreadsG,
          href: 'https://www.goodreads.com/user/show/113995266-manuel',
        },
        {
          icon: faLinkedinIn,
          href: 'https://www.linkedin.com/in/manuel-vargas-tapia-6ba3351a5/',
        },
        {
          icon: faEnvelope,
          href: 'mailto:manuelvargastapia@gmail.com',
        },
      ],
      navItems: [
        { title: 'Blog', to: '/' },
        { title: 'Apps', to: 'apps' },
        { title: 'Acerca de', to: 'about' },
      ],
      faBars,
    }
  },
}
</script>
