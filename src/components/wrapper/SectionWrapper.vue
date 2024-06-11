<script setup></script>

<template>
    <section>
        <div class="wrapper">
            <h2 class="section-title"><slot name="SectionName" /></h2>
            <slot />
        </div>
    </section>
</template>

<style lang="scss" scoped>
section {
    padding-block: 5rem;
}
.wrapper {
    max-width: 60rem;
    margin-inline: auto;
    padding-inline: 1rem;

    .section-title {
        font-size: 2.25rem;
    }
}
</style>
