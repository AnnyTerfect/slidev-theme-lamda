<script setup>
    import { defineProps } from 'vue'
    const props = defineProps({
        arrowFill: {
            type: String,
            default: 'none'
        },
    })

    function click(event) {
        console.log({
            clientX: event.clientX,
            clientY: event.clientY,
            x: event.clientX - event.target.getBoundingClientRect().left,
            y: event.clientY - event.target.getBoundingClientRect().top,
        })
    }
</script>

<template>
	<svg
        class="absolute top-0 left-0 w-1/1 h-1/1"
        viewBox="0 0 1600 900"
        @click="click"
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
    </svg>
</template>
