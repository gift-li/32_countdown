<script setup>
defineProps({
    counter: Number,
});
</script>

<template>
    <div class="col-12">
        <h1
            class="display-1 fw-bold m-0 p-4 mx-auto border border-5 border-dark"
        >
            {{ counter }}
        </h1>
    </div>
</template>

<style scoped>
h1 {
    max-width: fit-content;
}
</style>
