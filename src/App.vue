<script setup>
import { ref, watch } from "vue";
import data from "./assets/data.json";
import Number from "./components/Number.vue";
import Operation from "./components/Operation.vue";
import Toolbar from "./components/Toolbar.vue";

let counter = ref(32);
let operations = ref(["x", "+", "+", "+"]);

function random_choose(array) {
    return array[Math.floor(Math.random() * array.length)];
}

function updateCounter(newVal) {
    counter.value = newVal;
    operations.value = random_choose(data[counter.value]["operation"]);
}
</script>

<template>
    <main class="container vh-100 vw-100">
        <div
            class="row h-100 mx-5 p-5 justify-content-center align-items-center"
        >
            <div class="col=12 text-center">
                <Number :counter="counter" />
            </div>
            <div class="col=12 text-center">
                <Operation :operations="operations" />
            </div>
            <div class="col=12 text-center">
                <Toolbar :counter="counter" @update:counter="updateCounter" />
            </div>
        </div>
    </main>
</template>

<style scoped></style>
