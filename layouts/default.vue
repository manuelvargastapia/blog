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
    <v-footer app> </v-footer>
  </v-app>
</template>
