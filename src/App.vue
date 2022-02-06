<template>
  <v-app>
    <v-app-bar app dense color="#008c69" dark>
      <v-spacer></v-spacer>
      <v-btn href="/" target="_blank" text>
        <span class="mr-2">Button</span>
        <v-icon>mdi-open-in-new</v-icon>
      </v-btn>
    </v-app-bar>

    <v-main>
      <router-view />
    </v-main>
  </v-app>
</template>

<script>
export default {
  name: 'App',

  data: () => ({
    //
  }),
}
</script>
