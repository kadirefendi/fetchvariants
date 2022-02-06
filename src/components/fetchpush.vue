<template>
  <div>
    <v-row>
      <v-col cols="6">
        Text any item
        <v-text-field
          label="Input"
          @keypress.enter="addPush"
          v-model="addentry"
          class="mt-6"
        ></v-text-field>
      </v-col>
      <v-col cols="6">
        Items Table
        <v-simple-table>
          <template v-slot:default>
            <thead>
              <tr>
                <th class="text-left">Index</th>
                <th class="text-left">Item</th>
              </tr>
            </thead>
            <tbody>
              <tr v-for="(item, index) in inputfetch" :key="item">
                <td>{{ index }}</td>
                <td>{{ item }}</td>
              </tr>
            </tbody>
          </template>
        </v-simple-table>
      </v-col>
    </v-row>
  </div>
</template>

<script>
export default {
  data: () => ({
    addentry: null,
    inputfetch: [],
  }),
  methods: {
    addPush() {
      this.inputfetch.push(this.addentry)
      this.addentry = null
    },
  },
}
</script>
