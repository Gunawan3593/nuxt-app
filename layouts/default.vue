<template>
  <v-app>
    <v-main>
      <v-toolbar color="indigo" dark>
        <v-app-bar-nav-icon></v-app-bar-nav-icon>
        <v-toolbar-title>
          <nuxt-link to="/">
            Learning NuxtJS
          </nuxt-link>
        </v-toolbar-title>
        <v-spacer></v-spacer>
        <v-toolbar-items class="hidden-sm-and-down">
          <v-btn text><nuxt-link to="/weather-app">Weather App</nuxt-link></v-btn>
        </v-toolbar-items>
      </v-toolbar>
      <transition>
      <nuxt />
      </transition>
    </v-main>
  </v-app>
</template>

<script>
export default {
}
</script>

<style>
 a {
   text-decoration: none;
   color: white !important;
 }
</style>