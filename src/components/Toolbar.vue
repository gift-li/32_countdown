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
    <div class="col-12 d-flex justify-content-center align-items-center">
        <button class="btn btn-lg btn-primary" @click.prevent="countdown">
            countdown<i class="bi bi-play-fill ms-1"></i>
        </button>
        <button class="btn btn-lg btn-secondary ms-5" @click.prevent="pause">
            pause<i class="bi bi-pause ms-1"></i>
        </button>
    </div>
</template>

<style scoped></style>
