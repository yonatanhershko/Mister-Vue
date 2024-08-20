<template>
    <p :style="{ color: timerColor }">{{ timer }}</p>
</template>

<script>
import { utilService } from "../services/util.service.js"

export default {
    data() {
        return {
            timer:15,
            intervalId: null

        }
    }
}
</script>

<style lang="scss">

p {
  font-size: 24px;
  font-weight: bold;
}
</style>