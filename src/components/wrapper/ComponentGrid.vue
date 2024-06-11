<template>
    <div class="grid">
        <slot />
    </div>
</template>

<script setup></script>

<style lang="scss" scoped>
.grid {
    display: grid;
    grid-template-columns: 1fr 1fr 1fr;
    gap: 2rem;
}
</style>
