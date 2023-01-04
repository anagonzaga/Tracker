<template>
    <div class="box has-text-weight-bold">
        <slot></slot>
    </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue'

export default defineComponent({
   name: 'boxTracker',
})
</script>

<style scoped>
    .box{ background-color: #C4FCF0;}
</style>
