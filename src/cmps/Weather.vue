<template>
  <div v-on:click="isDarkMode = !isDarkMode" v-bind:class="mode"><!-- toggle here -->
    <img v-bind:src="`./src/assets/imgs/seasons/${getCurrSeason}.png`" alt="he" />
    <p>{{ getCurrSeason }}</p>
    <p>{{ formattedTime }}</p>
  </div>
</template>

<script>
import { utilService } from "../services/util.service.js"

export default {
  data() {
    // save states here
    return {
      currentTime: new Date(),
      isDarkMode: true,
    }
  },
  computed: {
    // math place just to show
    formattedTime() {
      return this.currentTime.toLocaleTimeString()
    },
    getCurrSeason() {
      return utilService.getSeason(this.currentTime).toLowerCase()

    },
    mode() {
      return {
        dark: this.isDarkMode,
        light: !this.isDarkMode
      }
    }

  },
  created() {
    // like use effect for code like js
    this.updateTime()
    this.timer = setInterval(this.updateTime, 1000)
  },
  mounted() {
    // for all the elements html like input focus
  },
  unmount() {
    //when close the cmp
    clearInterval(this.timer)
  },
  methods: {
    // functions like crud
    updateTime() {
      this.currentTime = new Date()
    },
  },
}
</script>

<style lang="scss">
img {
  height: 150px;
  width: 150px;
}

.light {
  background-color: rgb(58, 126, 146);
}

.dark {
  background-color: rgb(21, 38, 43);
}
</style>