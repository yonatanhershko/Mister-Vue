<template>
    <h1>{{ watcher.fullname }}</h1>
    <img :src="`../src/assets/imgs/seasons/users/${watcher.profileImg}`" alt="">
</template>
<script>

export default {
    props: ['watcher'],
}

</script>

<style></style>