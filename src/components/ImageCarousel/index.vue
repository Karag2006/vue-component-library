<script setup>
import { ref } from 'vue'
import MediaElement from './MediaElement.vue'

const images = [
    'https://images.unsplash.com/photo-1640948612546-3b9e29c23e98?crop=entropy&cs=tinysrgb&fit=max&fm=jpg&ixid=MnwxNDU4OXwwfDF8cmFuZG9tfHx8fHx8fHx8MTY0MzM5ODc5NQ&ixlib=rb-1.2.1&q=80&w=400',
    'https://images.unsplash.com/photo-1641118961077-440391095cdc?crop=entropy&cs=tinysrgb&fit=max&fm=jpg&ixid=MnwxNDU4OXwwfDF8cmFuZG9tfHx8fHx8fHx8MTY0MzM5ODc2Mw&ixlib=rb-1.2.1&q=80&w=400',
    'https://images.unsplash.com/photo-1642190672487-22bde32965f7?crop=entropy&cs=tinysrgb&fit=max&fm=jpg&ixid=MnwxNDU4OXwwfDF8cmFuZG9tfHx8fHx8fHx8MTY0MzM5ODcyOA&ixlib=rb-1.2.1&q=80&w=400',
    'https://images.unsplash.com/photo-1641841344411-49dbd02896f4?crop=entropy&cs=tinysrgb&fit=max&fm=jpg&ixid=MnwxNDU4OXwwfDF8cmFuZG9tfHx8fHx8fHx8MTY0MzM5ODcyOA&ixlib=rb-1.2.1&q=80&w=400'
]

const current = ref(1)
const setCurrent = (value) => {
    current.value = value
}
</script>

<template>
    <div class="media-container">
        <div class="media-scroller">
            <MediaElement
                v-for="(image, index) in images"
                :key="index"
                :id="index + 1"
                :max="images.length"
                :image="image"
                :current="current"
                @changeCurrent="setCurrent"
            />
        </div>
        <div class="navigation-indicators">
            <div
                v-for="(image, index) in images"
                :class="index + 1 === current ? 'current' : ''"
                :key="`indicator-${index}`"
            ></div>
        </div>
    </div>

    <svg>
        <symbol id="next" viewBox="0 0 256 512">
            <path
                fill="white"
                d="M224.3 273l-136 136c-9.4 9.4-24.6 9.4-33.9 0l-22.6-22.6c-9.4-9.4-9.4-24.6 0-33.9l96.4-96.4-96.4-96.4c-9.4-9.4-9.4-24.6 0-33.9L54.3 103c9.4-9.4 24.6-9.4 33.9 0l136 136c9.5 9.4 9.5 24.6.1 34z"
            />
        </symbol>

        <symbol id="previous" viewBox="0 0 256 512">
            <path
                fill="white"
                d="M31.7 239l136-136c9.4-9.4 24.6-9.4 33.9 0l22.6 22.6c9.4 9.4 9.4 24.6 0 33.9L127.9 256l96.4 96.4c9.4 9.4 9.4 24.6 0 33.9L201.7 409c-9.4 9.4-24.6 9.4-33.9 0l-136-136c-9.5-9.4-9.5-24.6-.1-34z"
            />
        </symbol>
    </svg>
</template>

<style lang="scss">
.media-container {
    position: relative;
    display: grid;
    place-items: center;
}

.media-scroller,
.media-group {
    display: grid;
    gap: 0.25rem;
    grid-auto-flow: column;
}

.media-scroller {
    overflow-x: hidden;
    scroll-behavior: smooth;
    grid-auto-columns: 100%;
    padding: 0 3rem;
    scroll-padding-inline: 3rem;
}

.media-group {
    margin-top: auto;
    grid-auto-columns: 1fr;
}

.media-element {
    border-radius: 0.25rem;
    overflow: hidden;
}

.media-element > img {
    width: 100%;
    aspect-ratio: 1;
    object-fit: cover;
}

.next,
.previous {
    display: none;
    align-items: center;
    z-index: 10;
    position: absolute;
    width: 3rem;
    padding: 1rem;
    background: rgb(0 0 0 / 0);
    opacity: 0;
}

.previous {
    left: 0;
    top: 0;
    bottom: 0;
}

.next {
    right: 0;
    top: 0;
    bottom: 0;
}

.media-group:first-child :where(.next, .previous) {
    display: flex;
}

.media-scroller:hover :where(.next, .previous) {
    opacity: 1;
}

:where(.next, .previous):hover {
    background: rgb(0 0 0 / 0.3);
}

:where(.next, .previous) > svg {
    transition: transform 75ms linear;
    transform: scale(1);
}
:where(.next, .previous):hover > svg {
    transform: scale(1.2);
}

.media-group:target :where(.next, .previous) {
    display: flex;
}

.media-scroller:has(:target:not(:first-child))
    .media-group:first-of-type
    .next {
    display: none;
}

/* navigation indicators */

.navigation-indicators {
    display: flex;
    gap: 3px;
}

.navigation-indicators > * {
    width: 1rem;
    height: 2px;
    background: white;
    opacity: 0.5;
}

.media-scroller:has(.media-group:target)
    .navigation-indicators
    > *:nth-child(1) {
    opacity: 0.5;
}

.navigation-indicators > .current {
    opacity: 1;
}
</style>
