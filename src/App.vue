<template>
  <header>
    <nav>
      <button v-on:click="route = 'Weather'">Weather</button>
      <button v-on:click="route = 'CountDown'">CountDown</button>
      <button v-on:click="route = 'Watcher'">Watcher</button>
      <button v-on:click="route = 'MouseMonitor'">MouseMonitor</button>
    </nav>
  </header>

  <Weather v-if="route === 'Weather'" />
  <Watcher v-if="route === 'Watcher'" />
  <MouseMonitor v-if="route === 'MouseMonitor'" />
  <CountDown  v-on:due="inHere"  v-if="route === 'CountDown'" />
</template>

<script>
import Weather from "./cmps/Weather.vue";
import CountDown from "./cmps/CountDown.vue";
import Watcher from "./cmps/Watcher.vue";
import MouseMonitor from "./cmps/MouseMonitor.vue";
export default {
  components: {
    Weather,
    CountDown,
    Watcher,
    MouseMonitor
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