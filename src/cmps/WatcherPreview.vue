<template>
    <h1 class="name">{{ watcher.fullname }}</h1>
    <img :src="`../src/assets/imgs/seasons/users/${watcher.profileImg}`" alt="">
</template>
<script>

export default {
    props: ['watcher'],
}

</script>

<style></style>