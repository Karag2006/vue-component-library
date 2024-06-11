<template>
    <div class="component-view">
        <slot />
    </div>
</template>

<script lang="ts" setup></script>

<style>
.component-view {
    display: grid;
    place-items: center;
    height: 20rem;
    min-width: 15rem;
    border: 2px solid darkgray;
    border-radius: 5%;
}
</style>
