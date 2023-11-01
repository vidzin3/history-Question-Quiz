<script>
  import {RouterView} from 'vue-router'

  export default {
    components:{RouterView},
    data(){
      return{
        icons: [
          'mdi-facebook',
          'mdi-twitter',
          'mdi-linkedin',
          'mdi-instagram',
        ],
        shower:false
      }
    }
  }
</script>

<template>
  <v-app>
    <v-app-bar>
      <v-app-bar-nav-icon @click="shower = !shower"></v-app-bar-nav-icon>
      <v-app-bar-title>History Quiz</v-app-bar-title>
      <v-spacer></v-spacer>
      <v-list-item class="rounded-xl" to="/">HOME</v-list-item>
      <v-list-item class="rounded-xl" to="/about">ABOUT</v-list-item>
    </v-app-bar>
    <v-navigation-drawer v-model="shower">
      <h1 class=text-center>Merl ey ot mean ey te 😼</h1>
    </v-navigation-drawer>
    <v-main>
      <RouterView />
    </v-main>
    <v-footer class="d-flex flex-column pa-0 align-center justify-end">
      <div class="bg-teal d-flex w-100 align-center px-4 py-2">
        <strong>K-David ❤️</strong>

        <v-spacer></v-spacer>

        <v-btn
          v-for="icon in icons"
          :key="icon"
          class="mx-4"
          :icon="icon"
          variant="plain"
          size="small"
        ></v-btn>
      </div>
    </v-footer>
  </v-app>
</template>