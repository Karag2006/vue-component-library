<script setup>
import { ref } from 'vue'
import {
    LuCircleDot,
    LuCircle,
    LuArrowBigLeft,
    LuArrowBigRight
} from '@kalimahapps/vue-icons'

const props = defineProps({
    images: Array
})

const currentIndex = ref(0)
const endMarker = ref(null)

const skipControls = () => {
    endMarker.value.focus()
}

const nextSlide = () => {
    if (props.images && props.images.length > 0) {
        currentIndex.value = (currentIndex.value + 1) % props.images.length
    }
}

const prevSlide = () => {
    if (props.images && props.images.length > 0) {
        currentIndex.value =
            (currentIndex.value - 1 + props.images.length) % props.images.length
    }
}

const goToImage = (index) => {
    if (props.images && props.images.length > 0) currentIndex.value = index
}
</script>

<template>
    <section class="slider" aria-label="Image Slider">
        <button class="skip-link" @click="skipControls">
            Bilder Kontrollen überspringen
        </button>
        <div class="slider-image-container">
            <img
                v-for="(url, index) in props.images"
                :style="{ translate: `${-100 * currentIndex}%` }"
                :key="url"
                :src="url"
                :alt="`Container Bild ${index + 1} `"
                :aria-hidden="index !== currentIndex"
            />
        </div>

        <div v-if="props.images.length > 1" class="slider-controls">
            <button
                @click="prevSlide"
                class="nav prev"
                aria-label="Auf vorheriges Bild wechseln"
            >
                <LuArrowBigLeft aria-hidden />
            </button>
            <button
                @click="nextSlide"
                class="nav next"
                aria-label="Auf nächstes Bild wechseln"
            >
                <LuArrowBigRight aria-hidden />
            </button>
        </div>
        <div v-if="props.images.length > 1" class="indicators">
            <button
                v-for="(image, index) in props.images"
                :key="index"
                :class="{ active: index === currentIndex }"
                @click="goToImage(index)"
                :aria-label="`Auf Bild ${index + 1} wechseln`"
            >
                <LuCircle v-if="index !== currentIndex" aria-hidden />
                <LuCircleDot v-else aria-hidden />
            </button>
        </div>
        <div id="after-image-slider-controls" tabindex="-1" ref="endMarker" />
    </section>
</template>

<style lang="scss" scoped>
.slider {
    width: 100%;
    height: 100%;
    position: relative;
    img {
        display: block;
        width: 100%;
        height: 100%;
        object-fit: cover;
        transition: translate 300ms ease-in-out;
        flex-shrink: 0;
        flex-grow: 0;
    }

    &-image-container {
        width: 100%;
        height: 100%;
        display: flex;
        overflow: hidden;
    }
}

.nav {
    all: unset;
    --_hsl-clr-neutral-900: 0, 0%, 0%;
    --_alpha: 0.2;
    --_size: 2rem;

    display: block;
    position: absolute;
    top: 0;
    bottom: 0;
    padding: 1rem;
    cursor: pointer;
    transition: background-color 100ms ease-in-out;

    & > * {
        stroke: white;
        fill: black;
        height: var(--_size);
        width: var(--_size);
    }

    &:hover,
    &:focus-visible {
        background-color: hsla(var(--_hsl-clr-neutral-900), var(--_alpha));

        & > * {
            animation: squish 200ms ease-in-out;
        }
    }

    &:focus-visible {
        outline: auto;
    }

    @keyframes squish {
        50% {
            scale: 1.4 0.6;
        }
    }

    &.prev {
        left: 0;
    }
    &.next {
        right: 0;
    }
}

.indicators {
    --_color: var(--clr-neutral-800);
    --_active-color: var(--clr-neutral-900);
    --_size: 1rem;
    position: absolute;
    bottom: 0.5rem;
    left: 50%;
    translate: -50%;

    display: flex;
    justify-content: center;
    gap: calc(var(--_size) / 2);
    margin-block-start: 1rem;
    button {
        all: unset;
        display: block;
        cursor: pointer;
        width: var(--_size);
        height: var(--_size);
        transition: scale 100ms ease-in-out;

        &:hover,
        &:focus-visible {
            scale: 1.2;
        }

        &:focus-visible {
            outline: auto;
        }

        & > * {
            stroke: white;
            fill: black;
            width: 100%;
            height: 100%;
        }
    }
}

.skip-link {
    position: absolute;
    width: 1px;
    height: 1px;
    padding: 0;
    margin: -1px;
    overflow: hidden;
    border: 0;
    clip: rect(0, 0, 0, 0);

    &:focus-visible {
        top: 0;
        left: 0;

        width: auto;
        height: auto;
        padding: 0.5rem;
        margin: 0;

        border: 1px solid black;
        background-color: white;
        text-decoration: none;
        color: black;
        clip: unset;
        z-index: 100;
    }
}
</style>
