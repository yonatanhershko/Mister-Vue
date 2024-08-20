<template>
  <header>
    <nav>
      <button v-on:click="route = 'Weather'">Weather</button>
      <button v-on:click="route = 'CountDown'">CountDown</button>
      <!-- <button v-on:click="route = 'PetIndex'">PetIndex</button> -->
    </nav>
  </header>

  <Weather v-if="route === 'Weather'" />
  <CountDown  v-on:due="inHere"  v-if="route === 'CountDown'" />
</template>

<script>
import Weather from "./cmps/Weather.vue";
import CountDown from "./cmps/CountDown.vue";
export default {
  components: {
    Weather,
    CountDown
  },

  data() {
    return {
      route: "",
    };
  },
  methods: {
    inHere() {
      console.log('hey mama')
    }
  }
};
</script>

<style lang="scss"></style>