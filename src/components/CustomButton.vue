<script setup>
import { computed } from 'vue'
import { mergeClassnames } from '@/lib/utils'

const props = defineProps({
    variant: String,
    size: String,
    class: String
})

const variantClass = computed(() => {
    if (props.variant) return `button-variant-${props.variant}`
    return ''
})

const sizeClass = computed(() => {
    if (props.size) return `button-size-${props.size}`
    return ''
})

const buttonClass = computed(() => {
    return mergeClassnames([
        'button',
        variantClass.value,
        sizeClass.value,
        props.class
    ])
})
</script>

<template>
    <button :class="buttonClass">
        <span class="button-prefix">
            <slot name="prefix" />
        </span>
        <slot />
        <span class="button-sufix">
            <slot name="sufix" />
        </span>
    </button>
</template>

<style lang="scss" scoped>
.button {
    display: flex;
    gap: 0.5rem;
    border-radius: 0.5rem;
    align-items: center;
    justify-content: center;

    &-variant-test {
        color: var(--vt-c-black);
        background-color: var(--vt-c-red);
    }
    &-variant-outline {
        color: var(--vt-c-white-mute);
        border: 1px solid var(--vt-c-white-mute);
        background: transparent;
    }

    &-size-sm {
        padding-inline: 0.5rem;
        padding-block: 0.25rem;
    }
    &-size-md {
        padding-inline: 0.75rem;
        padding-block: 0.5rem;
        font-size: 1.1rem;
    }
}
</style>
