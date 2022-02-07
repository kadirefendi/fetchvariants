<template>
  <div>
    <v-row>
      <v-col cols="6">
        Text any item
        <v-text-field
          label="Input"
          @keypress.enter.prevent="itemFetchPost"
          v-model="itemsync"
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
              <tr v-for="item in items" :key="item.id">
                <td>{{ item.id }}</td>
                <td>{{ item.item }}</td>
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
    items: [],
    itemsync: '',
  }),
  async created() {
    await fetch('http://localhost:3000/data')
      .then((res) => res.json())
      .then((data) => (this.items = data))
  },

  methods: {
    itemFetchPost() {
      console.log(this.itemsync)
      fetch('http://localhost:3000/data', {
        method: 'POST',
        headers: {
          'Content-Type': 'application/json',
        },
        body: JSON.stringify({
          item: this.itemsync,
        }),
      }).then((res) => res.json())
    },
  },
}
</script>
