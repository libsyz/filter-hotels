<template>
  <div id="app">
    <h1> Vue Filter Demo </h1>
    <div class="filter-container">
      <div class="filter-header"> Filter Hotels </div>
      <filter-dialogue/>
    </div>

    <hotels-list/>
  </div>
</template>

<script>
import HotelsList from './components/HotelsList.vue'
import FilterDialogue from './components/FilterDialogue.vue'

export default {
  name: 'app',
  components: {
    FilterDialogue,
    HotelsList
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;

}

.filter-container {
  display: flex;
  justify-content: space-around;
  padding-bottom: 20px;
  text-transform: uppercase;
  font-weight: bolder;
}

body {
  background-color: #41B883;
}
</style>
