<template>
    <div class="monitor-container">
        <h3>Mouse Position</h3>
        <h4 v-if="isOn">X: {{ pos.x }}, Y: {{ pos.y }}</h4>
        <h4 v-else>X: {{ pos.x }}, Y: {{ pos.x }}</h4>

        <button class="pos-btn" v-on:click="changeIsOn">{{ btnText }}</button>
    </div>
</template>

<script>
export default {
    data() {
        return {
            isOn: true,
            pos: { x: 0, y: 0 },
            btnText: 'Stop'
        }
    },

    created() {

        if (this.isOn) {
            document.addEventListener('mousemove', this.handleMouseMove)
        }
    },
    unmounted() {
        document.removeEventListener('mousemove', this.handleMouseMove);
    },
    methods: {
        handleMouseMove(event) {
            this.pos = {
                x: event.clientX, y: event.clientY
            }
        },
        changeIsOn() {
            this.isOn = !this.isOn;
            this.btnText = this.isOn ? 'Stop' : 'Start';

            if (this.isOn) {
                document.addEventListener('mousemove', this.handleMouseMove);
            } else {
                document.removeEventListener('mousemove', this.handleMouseMove);
            }
        },
    }
}
</script>

<style lang="scss">
.pos-btn {
    height: 50px;
    width: 50px;
}
</style>