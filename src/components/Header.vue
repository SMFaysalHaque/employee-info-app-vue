<template>
    <div>
        <p class="text-red-700">{{ name }}</p>
    </div>
</template>

<script>
    export default {
        name: 'Header',
        // props: ['title'], // this is a way to write props
        props: {
            name: String, // this is a way to write props
        }
    }
</script>

<style scoped>

</style>