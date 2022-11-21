<script setup>
import { ref } from "vue";
import data from "./assets/data.json";
import Number from "./components/Number.vue";
import Operation from "./components/Operation.vue";
import Toolbar from "./components/Toolbar.vue";

let counter = ref(32);
let operations = ref(["x", "+", "+", "+"]);

function ramdomChoose(array) {
    return array[Math.floor(Math.random() * array.length)];
}

function updateCounter(newVal) {
    counter.value = newVal;
    operations.value = ramdomChoose(data[counter.value]["operation"]);
}
</script>

<template>
    <main
        class="container h-100 d-flex justify-content-center align-items-center"
    >
        <div class="row">
            <Number :counter="counter" />
            <Operation :operations="operations" />
            <Toolbar :counter="counter" @update:counter="updateCounter" />
        </div>
    </main>
</template>

<style scoped></style>
