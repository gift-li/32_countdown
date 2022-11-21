<script setup>
import { watch, ref } from "vue";

const props = defineProps({
    operations: Array,
});

const op1 = ref("text-warning");
const op2 = ref("text-primary");
const op3 = ref("text-primary");
const op4 = ref("text-primary");

// flip operation
function flip(flipOperation, newVal, cl) {
    const topHalf = flipOperation.querySelector(".top");
    const oldOperation = topHalf.textContent;
    if (newVal === oldOperation) return;

    const bottomHalf = flipOperation.querySelector(".bottom");
    // const topFlip = document.createElement("p");
    // topFlip.classList.add("top-flip");
    // const bottomFlip = document.createElement("p");
    // bottomFlip.classList.add("bottom-flip");

    // top.textContent = oldOperation;
    // bottomHalf.textContent = oldOperation;
    // topFlip.textContent = oldOperation;
    // bottomFlip.textContent = newVal;

    // topFlip.addEventListener("animationstart", (e) => {
    topHalf.textContent = newVal;
    // });
    // topFlip.addEventListener("animationend", (e) => {
    //     topFlip.remove();
    // });
    // bottomFlip.addEventListener("animationend", (e) => {
    bottomHalf.textContent = newVal;
    //     bottomFlip.remove();
    // });
    // flipOperation.append(topFlip, bottomFlip);

    switch (newVal) {
        case "+":
            cl.value = "text-primary";
        case "-":
            cl.value = "text-secondary";
        case "×":
            cl.value = "text-warning";
        case "÷":
            cl.value = "text-danger";
        default:
    }
}

// watch changes of props for operations
watch(
    () => props.operations,
    (newVal) => {
        flip(document.querySelector(".operation-1"), newVal[0], op1);
        flip(document.querySelector(".operation-2"), newVal[1], op2);
        flip(document.querySelector(".operation-3"), newVal[2], op3);
        flip(document.querySelector(".operation-4"), newVal[3], op4);
    }
);
</script>

<template>
    <div class="col-12 my-5 d-flex justify-content-center align-items-center">
        <p>6</p>
        <div class="operation operation-1" :class="op1">
            <p class="top">×</p>
            <p class="bottom">×</p>
        </div>
        <p>4</p>
        <div class="operation operation-2" :class="op2">
            <p class="top">+</p>
            <p class="bottom">+</p>
        </div>
        <p>5</p>
        <div class="operation operation-3" :class="op3">
            <p class="top">+</p>
            <p class="bottom">+</p>
        </div>
        <p>2</p>
        <div class="operation operation-4" :class="op4">
            <p class="top">+</p>
            <p class="bottom">+</p>
        </div>
        <p>1</p>
    </div>
</template>

<style scoped>
p {
    font-size: 7.5vh;
    margin: 0 1.5vw 0 1.5vw;
}
.operation {
    position: relative;
    min-height: 12vh;
    min-width: 8rem;
    display: inline-flex;
    flex-direction: column;
    box-shadow: 0 2px 3px 0 rgba(0, 0, 0, 0.2);
    border-radius: 0.1em;
}

.top,
.bottom,
.operation .top-flip,
.operation .bottom-flip {
    height: 0.75em;
    line-height: 1;
    padding: 0.25em;
    overflow: hidden;
    display: flex;
    justify-content: center;
}

.top,
.operation .top-flip {
    background-color: #f7f7f7;
    border-top-right-radius: 0.1em;
    border-top-left-radius: 0.1em;
    border-bottom: 1px solid rgba(0, 0, 0, 0.1);
}

.bottom,
.operation .bottom-flip {
    background-color: white;
    display: flex;
    align-items: flex-end;
    border-bottom-right-radius: 0.1em;
    border-bottom-left-radius: 0.1em;
}

.operation .top-flip {
    position: absolute;
    width: 100%;
    animation: flip-top 250ms ease-in;
    transform-origin: bottom;
}

@keyframes flip-top {
    100% {
        transform: rotateX(90deg);
    }
}

.operation .bottom-flip {
    position: absolute;
    bottom: 0;
    width: 100%;
    animation: flip-bottom 250ms ease-out 250ms;
    transform-origin: top;
    transform: rotateX(90deg);
}

@keyframes flip-bottom {
    100% {
        transform: rotateX(0deg);
    }
}
</style>
