<template>
  <v-layout>
    <v-flex>
      <v-card>
        <!-- <img src="../assets/3redbooks-300px.png"> -->
        <v-card-title>

          <v-spacer></v-spacer>
          <v-spacer></v-spacer>
          <v-text-field append-icon="search" label="Search" single-line hide-details v-model="search"></v-text-field>
        </v-card-title>
        <v-data-table hide-actions v-bind:headers="headers" v-bind:items="books" v-bind:search="search">
          <template slot="items" slot-scope="props">
            <td class="text-xs-center">
              <a v-bind:href="props.item.bUrl" target=”_blank”>{{ props.item.bTitle }}</a>
            </td>
            <td class="text-xs-right">{{ props.item.bAuthor }}</td>
            <td class="text-xs-right">{{ props.item.bGuest }}</td>
            <td class="text-xs-center">{{ props.item.bEpNumber }}</td>

            <td class="text-xs-right">
              <a v-bind:href="props.item.bShowNotes" target=”_blank”>Link to Show Notes</a>
            </td>
          </template>

        </v-data-table>
      </v-card>
    </v-flex>
  </v-layout>
</template>

<script>
import axios from "axios";
import api from "./api";

export default {
  name: 'Home',
  data() {
    return {
      msg: 'Welcome to Your HomePage',
      tmp: '',
      books: [],
      search: '',
      headers: [
        { text: 'Book Title', align: 'left', value: 'bTitle' },
        { text: 'Author', value: 'bAuthor' },
        { text: 'Guest', value: 'bGuest' },
        { text: 'Episode Number', value: 'bEpNumber' },
        { text: 'Show Notes', sortable: false, value: 'bShowNotes' }
      ],
      items: [
        {
          value: false,
          name: 'Frozen Yogurt',
          calories: 159,
          fat: 6.0,
          carbs: [24, 36, 22, 55],
          protein: 4.0,
          sodium: 87,
          calcium: '14%',
          iron: 'http://www.test.com'
        },
        {
          value: false,
          name: 'Ice cream sandwich',
          calories: 237,
          fat: 9.0,
          carbs: 37,
          protein: 4.3,
          sodium: 129,
          calcium: '8%',
          iron: 'http://www.test1.com'
        },
        {
          value: false,
          name: 'Eclair',
          calories: 262,
          fat: 16.0,
          carbs: 23,
          protein: 6.0,
          sodium: 337,
          calcium: '6%',
          iron: 'http://www.test2.com'
        },
        {
          value: false,
          name: 'Cupcake',
          calories: 305,
          fat: 3.7,
          carbs: 67,
          protein: 4.3,
          sodium: 413,
          calcium: '3%',
          iron: 'http://www.test3.com'
        },
        {
          value: false,
          name: 'Gingerbread',
          calories: 356,
          fat: 16.0,
          carbs: 49,
          protein: 3.9,
          sodium: 327,
          calcium: '7%',
          iron: 'http://www.test4.com'
        },
        {
          value: false,
          name: 'Jelly bean',
          calories: 375,
          fat: 0.0,
          carbs: 94,
          protein: 0.0,
          sodium: 50,
          calcium: '0%',
          iron: 'http://www.test5.com'
        },
        {
          value: false,
          name: 'Lollipop',
          calories: 392,
          fat: 0.2,
          carbs: 98,
          protein: 0,
          sodium: 38,
          calcium: '0%',
          iron: 'http://www.test6.com'
        },
        {
          value: false,
          name: 'Honeycomb',
          calories: 408,
          fat: 3.2,
          carbs: 87,
          protein: 6.5,
          sodium: 562,
          calcium: '0%',
          iron: 'http://www.test7.com'
        },
        {
          value: false,
          name: 'Donut',
          calories: 452,
          fat: 25.0,
          carbs: 51,
          protein: 4.9,
          sodium: 326,
          calcium: '2%',
          iron: 'http://www.test8.com'
        },
        {
          value: false,
          name: 'KitKat',
          calories: 518,
          fat: 26.0,
          carbs: 65,
          protein: 7,
          sodium: 54,
          calcium: '12%',
          iron: 'http://www.test9.com'
        }
      ]
    }
  },
  created() {
    // function that GETS books from API
    api.getBooks().then(books => {
      this.books = books;
    });
  },
  computed: {
    //function to place items within an array each on their own line
    newLineWithinCell() {

    }
  }

}

</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1,
h2 {
  font-weight: normal;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  display: inline-block;
  margin: 0 10px;
}

a {
  color: #42b983;
}

img {
  margin: 75px 0 40px 40%;
  width: 20%;
}
</style>
