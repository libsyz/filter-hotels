<template>
  <div class="hello">
    <table>
      <thead>
        <tr>
          <td class="col-head">
            Name
          </td>
          <td class="col-head">
            Rating
          </td>
          <td class="col-head">
            Price
          </td>
          <td class="col-head">
            Description
          </td>
        </tr>
      </thead>
      <tbody>
        <tr v-for= "hotel in hotels"
            :key="hotel.id">
          <td class="name">
            <p>{{ hotel.name }}</p>
          </td>
          <td class="rating">
            <p>{{ hotel.rating }}</p>
          </td>
          <td class="price">
            <p>{{ hotel.price + " $"}}</p>
          </td>
          <td class="description"
              v-html="shorten(hotel.description)">
          </td>

        </tr>
      </tbody>
    </table>

  </div>
</template>

<script>

import { hotelsList } from './../assets/hotels_list.js'
import { bus } from './../main.js'

export default {
  name: 'hotels-list',
  props: {
    msg: String
  },
  created() {
    bus.$on('filtered', (data) => {
      this.hotels = data;
    })
  },
  data: () => {
    return {
      hotels: hotelsList
    }
  },
  methods: {
    shorten(text) {
      return text.split(" ")
                 .slice(0, 20)
                 .join(" ") + "..."
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

table {
  min-width: 600px;
  margin: 0 auto;
  background-color: #fff;
  border-radius: 5px;
  box-shadow: 11px 10px 16px -10px rgba(0,0,0,0.5),
              -11px 10px 16px -10px rgba(0,0,0,0.5);

}

.col-head {
  color: rgb(140, 140, 140);
  font-weight: bold;
}


tr {
  height: 48px;
  text-align: left;
}

td {
  padding: 0px 16px;
  text-align: center;
  border-bottom: solid 1px rgb(220, 220, 220);
}


tr:last-child > td {
  border-bottom: none;
}

.description {
  padding: 0px 90px;
}




h3 {
  margin: 40px 0 0;
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
</style>
