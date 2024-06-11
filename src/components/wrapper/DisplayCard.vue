<script setup></script>

<template>
    <div class="display-card">
        <div class="display-card--header">
            <slot name="header" />
        </div>
        <div class="display-card--content">
            <slot />
        </div>
        <div class="display-card--footer">
            <slot name="footer" />
        </div>
    </div>
</template>

<style lang="scss" scoped>
.display-card {
    display: grid;
    gap: 2rem;
    place-items: center;
    border: 4px solid white;

    &--content {
        display: grid;
        place-items: center;
        margin-inline: 1rem;
        height: 20rem;
        min-width: 15rem;
        border: 2px solid darkgray;
        border-radius: 20px;
    }

    &--header {
        padding: 1rem;
        font-weight: 600;
    }

    &--footer {
        padding: 1rem;
        background-color: white;
        color: black;
    }
}
</style>
