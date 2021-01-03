<template>
  <v-app-bar app flat absolute color="transparent">
    <v-toolbar-title>Manuel Vargas</v-toolbar-title>
    <v-spacer></v-spacer>
    <div class="d-none d-md-block">
      <v-container>
        <v-row align="center">
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
</template>

<script>
export default {
  props: {
    faBars: {
      type: [Object],
      required: true,
    },
    navItems: {
      type: [Array],
      required: true,
    },
  },
}
</script>
