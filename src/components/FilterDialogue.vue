<template lang="html">

  <section class="filter-dialogue">
    <input type="text" v-model="rating" placeholder="min rating">
    <input type="text" v-model="price" placeholder="min price">
    <div @click="filter()" class="filter">
      <img :src="filterLogo" alt="">
    </div>
  </section>

</template>

<script lang="js">

import { hotelsList } from './../assets/hotels_list.js';
import { bus } from './../main.js'

  export default  {
    name: 'filter-dialogue',
    props: [],
    mounted () {

    },
    data () {
      return {
        filterLogo: require('./../assets/filter.png'),
        price: "",
        rating: "",
        filteredHotels: [],
        hotels: hotelsList
      }
    },
    methods: {
      filter() {
        this.filterByPrice();
        this.filterByRating();
        bus.$emit('filtered', this.filteredHotels);
      },

      filterByPrice() {
        this.filteredHotels = this.minFilter(this.price, this.hotels, "price");
      },

      filterByRating() {
        this.filteredHotels = this.minFilter(this.rating, this.filteredHotels, "rating")
      },

      minFilter(input, array, property) {
          let min = parseInt(input);
            if (parseInt(input)) {
              return array.filter((el) => {
                return el[property] > min;
              });
          }
          else {
            return array
          }
        }

    },
    computed: {
    }
}

</script>

<style scoped>
  .filter-dialogue {
    display: flex;
  }
  .filter:hover {
    background-color: yellow;
    cursor: pointer;
  }

  img {
    height: 20px;
  }

  .filter {
    border-radius: 3px;
    padding: 5px 15px;
    background-color: rgb(240, 240, 240);
  }
</style>
