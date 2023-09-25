<template>
  <v-app>
 <v-app-bar color="#007bff">
  <v-app-bar-title>My Contacts App</v-app-bar-title>
 </v-app-bar>
    <v-main>
      <router-view/>
    </v-main>
  </v-app>
</template>

<script lang="ts">
import { defineComponent } from 'vue'

export default defineComponent({
  name: 'App',

  data () {
    return {
      //
    }
  },
})
</script>
