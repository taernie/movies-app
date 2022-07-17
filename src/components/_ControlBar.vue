<script setup lang="ts">

    const emit = defineEmits<{
        (event: "add-count", num: number) : void,
        (event: "reset-count") : void,
        (event: "subtract-count", num: number) : void
    }>();

</script>

<template>

    <button
        @click="emit('add-count', 4)"
    >Add</button>

    <button
        @click="emit('subtract-count', 2)"
    >Subtract</button>

    <button
        @click="emit('reset-count')"
    >Reset Count</button>

</template>