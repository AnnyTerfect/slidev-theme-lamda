<script setup>
    import { ref, defineProps, computed, onMounted } from 'vue'

    const props = defineProps({
        arrowFill: {
            type: String,
            default: 'none'
        },
        debug: {
            type: Boolean,
            default: false
        }
    })

    // SVG auto resize to page size
    const svg = ref(null)
    
    // Mouse position
    const mouse = ref({ x: 0, y: 0 })
    function mousemove(event) {
        mouse.value.x = event.offsetX
        mouse.value.y = event.offsetY
    }
</script>

<template>
	<svg
        ref="svg"
        class="absolute top-0 left-0 w-1/1 h-1/1"
        :viewBox="svg ? `0 0 ${svg.clientWidth} ${svg.clientHeight}` : '0 0 0 0'"
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
            <text>
                <tspan x="1rem" y="1rem" fill="black" font-size="1rem">x = {{ mouse.x }}</tspan>
                <tspan x="6rem" y="1rem" fill="black" font-size="1rem">y = {{ mouse.y }}</tspan>
            </text>
            <line :x1="mouse.x" :x2="mouse.x" :y1="0" :y2="svg ? svg.clientHeight : 0" stroke="black"></line>
            <line x1="0" :x2="svg ? svg.clientWidth : 0" :y1="mouse.y" :y2="mouse.y" stroke="black"></line>
        </g>
    </svg>
</template>