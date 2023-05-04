<script setup>
import { ref } from 'vue'

const props = defineProps({
    arrowFill: {
        type: String,
        default: 'black'
    },
    debug: {
        type: Boolean,
        default: false
    }
})

const svg = ref(null)
const width = ref(1600), height = ref(900)

// Mouse 
const mouse = ref({ x: 0, y: 0 })
function mousemove(event) {
    console.log(event.offsetX, svg.value.clientWidth, width.value)
    mouse.value.x = event.offsetX / svg.value.clientWidth * width.value
    mouse.value.y = event.offsetY / svg.value.clientHeight * height.value
}
</script>

<template>
	<svg
        ref="svg"
        class="absolute top-0 left-0 w-1/1 h-1/1"
        :viewBox="`0 0 ${width} ${height}`"
        @mousemove="mousemove"
    >
        <defs>
            <marker
                id="arrow"
                viewBox="0 0 10 10"
                refX="5"
                refY="5"
                markerUnits="strokeWidth"
                markerWidth="4"
                markerHeight="4"
                orient="auto">
                <path d="M 0 0 L 10 5 L 0 10 z" :fill="`${arrowFill}`" />
            </marker>
        </defs>
        <slot></slot>
        
        <g v-if="debug">
            <line class="stroke-red-500" :x1="mouse.x" :x2="mouse.x" :y1="0" :y2="height"></line>
            <line class="stroke-red-500" x1="0" :x2="width" :y1="mouse.y" :y2="mouse.y"></line>
            <text
                :x="mouse.x < width / 2 ? mouse.x + 5 : mouse.x - 5"
                :y="mouse.y < height / 2 ? mouse.y + 5 : mouse.y - 10"
                class="fill-red-500 text-0.5em mix-blend-diff"
                :style="{ textAnchor: mouse.x < width / 2 ? 'start' : 'end', dominantBaseline: mouse.y < height / 2 ? 'hanging' : 'baseline' }"
            >
                {{ mouse.x.toFixed(2) }}, {{ mouse.y.toFixed(2) }}
            </text>
        </g>
    </svg>
</template>