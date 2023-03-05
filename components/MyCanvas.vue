<script setup>
    import { ref, defineProps, computed } from 'vue'

    const svg = ref(null)

    const width = computed(() => {
        return svg.clientWidth ? svg.clientWidth : 16
    })
    const height = computed(() => {
        return svg.clientHeight ? svg.clientHeight: 9
    })

    const props = defineProps({
        arrowFill: {
            type: String,
            default: 'none'
        },
    })
</script>

<template>
	<svg
        ref="svg"
        class="absolute top-0 left-0 w-1/1 h-1/1"
        :viewBox="`0 0 ${width} ${height}`"
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