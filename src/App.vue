<template>
  <header>
    <nav>
      <button v-on:click="route = 'Weather'">Weather</button>
      <!-- <button v-on:click="route = 'SimpleCounter'">SimpleCounter</button> -->
      <!-- <button v-on:click="route = 'PetIndex'">PetIndex</button> -->
    </nav>
  </header>

  <Weather v-if="route === 'Weather'" />
</template>

<script>
import Weather from "./cmps/Weather.vue";
export default {
  components: {
    Weather,
  },

  data() {
    return {
      route: "Weather",
    };
  },
};
</script>

<style lang="scss"

</style>