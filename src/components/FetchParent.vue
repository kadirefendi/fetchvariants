<template>
  <v-container>
    <v-row class="d-flex justify-center mt-12">
      <v-col cols="8">
        <v-card>
          <v-card-title class="text-center justify-center py-6">
            <h1 class="font-weight-bold text-h2">Data Fetch Variants</h1>
          </v-card-title>

          <v-tabs v-model="tab" background-color="transparent" grow>
            <v-tab v-for="i in items" :key="i">
              {{ i.item }}
            </v-tab>
          </v-tabs>

          <v-tabs-items v-model="tab">
            <v-tab-item>
              <v-card flat>
                <v-card-text> <fetchpush /> </v-card-text>
              </v-card>
            </v-tab-item>
            <v-tab-item>
              <v-card flat>
                <v-card-text> <fetchfetch /> </v-card-text>
              </v-card>
            </v-tab-item>
            <v-tab-item>
              <v-card flat>
                <v-card-text> <fetchaxios /> </v-card-text>
              </v-card>
            </v-tab-item>
          </v-tabs-items>
        </v-card>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
import fetchpush from './fetchpush.vue'
import fetchfetch from './fetchfetch.vue'
import fetchaxios from './fetchaxios.vue'
export default {
  name: 'HelloWorld',
  components: {
    fetchpush,
    fetchfetch,
    fetchaxios,
  },

  data: () => ({
    tab: null,

    items: [
      {
        item: 'push',
        text: 'fetchpush',
      },
      {
        item: 'fetch',
        text: 'Lorem ipsum dolor sit amet, t',
      },
      {
        item: 'axios',
        text: 'Lorem ipsum dolor sit amet, sed do eiusmod tempor incididunt',
      },
    ],
  }),
}
</script>
