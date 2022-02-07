<template>
  <div>
    <v-row>
      <v-col cols="6">
        Text any item
        <v-text-field
          label="Input"
          @keypress.enter="axiosFetchPost"
          v-model="itemsync.item"
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
import axios from 'axios'
export default {
  data: () => ({
    items: [],
    itemsync: {
      id: null,
      item: '',
    },
    newResult: null,
  }),
  mounted() {
    axios
      .get('http://localhost:3000/data')
      .then((res) => (this.items = res.data))
  },
  //   created() {
  //     axios('http://localhost:3000/data')
  //       .then((res) => res.json())
  //       .then((data) => console.log(data.data))
  //   },

  methods: {
    axiosFetchPost() {
      axios
        .post('http://localhost:3000/data', {
          item: this.itemsync.item,
        })
        .then((res) => res.data)
      this.items
      this.itemsync.item = ''
    },
  },
}
</script>
