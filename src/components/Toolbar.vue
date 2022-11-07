<script setup>
const props = defineProps({
    counter: Number,
});
const emits = defineEmits(["update:counter"]);

var interval = null;
function countdown() {
    let timer = 32;
    emits("update:counter", timer);

    interval = setInterval(() => {
        if (timer === 0) {
            clearInterval(interval);
        } else {
            timer--;
            emits("update:counter", timer);
        }
    }, 1000);
}
function pause() {
    clearInterval(interval);
}
</script>

<template>
    <div class="d-flex justify-content-around">
        <button class="btn btn-lg btn-primary" @click.prevent="countdown">
            start
        </button>
        <button class="btn btn-lg btn-secondary" @click.prevent="pause">
            pause
        </button>
    </div>
</template>

<style scoped></style>
