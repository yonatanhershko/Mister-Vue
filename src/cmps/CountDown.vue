<template>
    <p :style="{ color: timerColor }">{{ timer }}</p>
</template>

<script>
import { utilService } from "../services/util.service.js"

export default {
    data() {
        return {
            timer: 7,
            intervalId: null
        }
    },
    computed: {
        timerColor() {
            return this.timer <= 5 ? 'red' : 'black'
        }
    },
    created() {
        this.intervalId = setInterval(() => {
            if (this.timer <= 1) {
                clearInterval(this.intervalId)
                this.isDone()
                this.timer = 0
            } else {
                this.timer--
            }
        }, 1000)

    },

    methods:{
        isDone(){
            this.$emit('due')
        },
    }
}
</script>

<style lang="scss">
p {
    font-size: 24px;
    font-weight: bold;
}
</style>