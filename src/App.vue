<script setup>
import { ref } from "vue";
import data from "./assets/data.json";
import Number from "./components/Number.vue";
import Operation from "./components/Operation.vue";
import Toolbar from "./components/Toolbar.vue";

let counter = ref(32);
let number = ref(32);
let operation = ref([]);

function randomize(len) {
    return Math.random() % len;
}
function countdown() {
    this.counter.value--;
}
function reset() {
    this.counter.value = 32;
}

// export default {
//     components: ["Number", "Operation", "Toolbar"],
//     data() {
//         return {
//             counter: 32,
//             data: data,
//         };
//     },
//     methods: {
//         randomize(len) {
//             Math.random() % len;
//         },
//         countdown() {
//             this.counter--;
//         },
//         reset() {
//             this.counter = 32;
//         },
//     },
// };
</script>

<template>
    <main class="container vh-100 vw-100">
        <div class="row mx-5 p-5 justify-content-center">
            <div class="col">
                <Number />
            </div>
        </div>
        <div class="row mx-5 p-5 justify-content-center">
            <div class="col">
                <Operation />
            </div>
        </div>
        <div class="row mx-5 p-5 justify-content-center">
            <div class="col">
                <Toolbar />
            </div>
        </div>
    </main>
</template>

<style scoped></style>
