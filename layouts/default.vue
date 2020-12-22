<template>
  <v-app>
    <v-app-bar app flat light>
      <v-toolbar-title>Manuel Vargas</v-toolbar-title>
      <v-spacer></v-spacer>
      <v-btn icon>
        <v-icon color="black">mdi-brightness-4</v-icon>
      </v-btn>
      <v-btn to="/" nuxt text> Blog </v-btn>
      <v-btn to="/apps" nuxt text> Apps </v-btn>
      <v-btn to="/about" nuxt text> Acerca de </v-btn>
      <!-- <v-row justify="space-between" align="center">
      </v-row> -->
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
