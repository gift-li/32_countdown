<script setup>
const props = defineProps({
    operations: Array,
});
</script>

<template>
    <div class="d-flex justify-content-around align-items-center">
        <p>6</p>
        <p class="operation">{{ operations[0] }}</p>
        <p>4</p>
        <p class="operation">{{ operations[1] }}</p>
        <p>5</p>
        <p class="operation">{{ operations[2] }}</p>
        <p>2</p>
        <p class="operation">{{ operations[3] }}</p>
        <p>1</p>
    </div>
</template>

<style scoped>
p {
    font-size: 7vh;
}
.operation {
    font-size: 4.5vh;
}
</style>
