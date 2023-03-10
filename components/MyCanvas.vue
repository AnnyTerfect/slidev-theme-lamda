<script setup>
import { ref, computed, defineProps } from 'vue'

const svg = ref(null)
const mousePosition = ref({ x: 0, y: 0 })

const width = computed(() => {
    const [x, y, w, h] = props.viewBox.split(' ').map(Number)
    return w
})
const height = computed(() => {
    const [x, y, w, h] = props.viewBox.split(' ').map(Number)
    return h
})

const props = defineProps({
    debug: {
        type: Boolean,
        default: false,
    },
    viewBox: {
        type: String,
        required: true,
    },
})

function handleMouseMove(event) {
    mousePosition.value = {
        x: event.offsetX / svg.value.clientWidth * width.value,
        y: event.offsetY / svg.value.clientHeight * height.value,
    }
}
</script>

<template>
    <svg
        ref="svg"
        :viewBox="viewBox"
        @mousemove="handleMouseMove"
    >
        <slot></slot>
        
        <!--show mouse position-->
        <g :visibility="debug ? 'visible' : 'hidden'">
            <line
                x1="0"
                :y1="mousePosition.y"
                :x2="width"
                :y2="mousePosition.y"
                stroke="red"
                stroke-width="1"
            />
            <line
                :x1="mousePosition.x"
                y1="0"
                :x2="mousePosition.x"
                :y2="height"
                stroke="red"
                stroke-width="1"
            />
            <text
                :x="mousePosition.x < width / 2 ? mousePosition.x + 5 : mousePosition.x - 5"
                :y="mousePosition.y < height / 2 ? mousePosition.y + 5 : mousePosition.y - 10"
                class="fill-red-500 text-0.5em mix-blend-diff"
                :style="{ textAnchor: mousePosition.x < width / 2 ? 'start' : 'end', dominantBaseline: mousePosition.y < height / 2 ? 'hanging' : 'baseline' }"
            >
                {{ mousePosition.x.toFixed(2) }}, {{ mousePosition.y.toFixed(2) }}
            </text>
        </g>
    </svg>
</template>