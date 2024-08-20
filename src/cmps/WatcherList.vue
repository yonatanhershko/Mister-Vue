<template>
    <section>
        <h2 class='watcher-header'>Watcher App</h2>
        <div v-for="watcher in watchers" v-bind:key="watcher.id" v-on:click="selectWatcher(watcher)" class='watcher'>
            <WatcherPreview v-bind:watcher="watcher" />
            <button v-on:click="removeWatcher(watcher.id)">X</button>
            
        </div>
    </section>
</template>

<script>
import WatcherPreview from "./WatcherPreview.vue"

export default {
    props: ['watchers'],
    components: {
        WatcherPreview,
    },
    methods: {
        removeWatcher(watcherId) {
            const idx = this.watchers.findIndex(watcher => watcher.id === watcherId)
            this.watchers.splice(idx, 1)
        },
        selectWatcher(watcher) {
            return this.$emit('selectWatcher',watcher)
           
        },
    }

}
</script>

<style lang="scss"></style>