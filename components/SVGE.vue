<script setup>
import "mathjax-full/es5/tex-svg-full";
import { computed, useSlots } from 'vue'

const props = defineProps({
	scale: {
		type: Number,
		default: 100
	}
})

const $slots = useSlots()

const html = computed(() => {
	return window.MathJax.tex2svg($slots.default ? $slots.default()[0].children : '').innerHTML
})
</script>

<template>
	<svg>
		<g :style="`transform: scale(${scale / 100})`" v-html="html" :key="html"></g>
	</svg>
</template>

<style>
	.equation > svg{
		margin: auto;
	}
</style>