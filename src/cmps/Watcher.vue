<template>

    <button v-on:click="onAddWatcher">Add</button>
    <WatcherList v-bind:watchers="watchers" v-on:selectWatcher="selectWatcher" />
    <div v-if="selectedWatcher" class="movies">
        {{ selectedWatcher.movies }}

    </div>
</template>

<script>
import WatcherList from "./WatcherList.vue";

export default {
    components: {
        WatcherList
    },

    data() {
        return {
            watchers: [
                { id: 'w101', profileImg: 'profile1.png', fullname: 'Puki Ba', movies: ['Rambo', 'The GodFather'] },
                { id: 'w102', profileImg: 'profile2.png', fullname: 'Muki Pa', movies: ['Hairy Potter', 'Rocky'] },
                { id: 'w103', profileImg: 'profile3.png', fullname: 'Nuki Da', movies: ['ManSpider', 'Rocky'] }
            ],

            selectedWatcher: null
        }
    },
    methods: {
        onAddWatcher() {
            const id = Date.now() % 100
            const watcher = {
                id,
                fullname: `watcher${id}`,
                profileImg: 'profile1.png'
            }
            this.watchers.unshift(watcher)
        },
        selectWatcher(watcher) {
            this.selectedWatcher = watcher

        }
    },
}
</script>

<style lang="scss">
section {
    background-color: #f4f4f4;
    padding: 20px;
    border-radius: 8px;
    box-shadow: 0px 2px 8px rgba(0, 0, 0, 0.1);
    max-width: 600px;
    margin: 0 auto;

    button {
        background-color: #ff6b6b;
        color: white;
        border: none;
        border-radius: 4px;
        padding: 6px 12px;
        cursor: pointer;
        transition: background-color 0.2s;

        &:hover {
            background-color: #e55050;
        }
    }

    .watcher {
        display: flex;
        align-items: center;
        justify-content: space-between;
        background-color: #fff;
        padding: 10px 15px;
        margin-bottom: 10px;
        border-radius: 8px;
        box-shadow: 0px 1px 4px rgba(0, 0, 0, 0.1);
        transition: transform 0.2s, box-shadow 0.2s;

        .name {
            max-width:80px ;
        }

        &:hover {
            transform: translateY(-2px);
            box-shadow: 0px 4px 12px rgba(0, 0, 0, 0.15);
        }
    }
}

.movies {
    display: flex;
    align-items: center;
    text-align: center;
    justify-content: center;
    background-color: #b8f8e5;
    font-size: 22px;
}
</style>