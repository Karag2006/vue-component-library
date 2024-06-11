<script setup>
import { computed } from 'vue'

const props = defineProps({
    id: Number,
    max: Number,
    image: String,
    current: Number
})

const emit = defineEmits(['changeCurrent'])

const prev = () => {
    emit('changeCurrent', props.current - 1)
}

const next = () => {
    emit('changeCurrent', props.current + 1)
}

const previousElement = computed(() => props.id - 1)
const nextElement = computed(() => props.id + 1)
</script>

<template>
    <div class="media-group" :id="`group-${props.id}`">
        <a
            v-if="previousElement > 0"
            class="previous"
            :href="`#group-${previousElement}`"
            @click="prev"
        >
            <svg>
                <use href="#previous"></use>
            </svg>
        </a>

        <div class="media-element">
            <img :src="props.image" alt="" />
        </div>

        <a
            v-if="nextElement <= props.max"
            class="next"
            :href="`#group-${nextElement}`"
            aria-label="next"
            @click="next"
        >
            <svg>
                <use href="#next"></use>
            </svg>
        </a>
    </div>
</template>

<style lang="scss"></style>
