<script setup>
import "mathjax-full/es5/tex-svg-full";

const props = defineProps({
	fontSize: {
		type: String,
		default: '1em'
	},
})

const $slots = useSlots()

const html = computed(() => {
	return window.MathJax.tex2svg($slots.default ? $slots.default()[0].children : '').innerHTML
})
</script>


<template>
	<span class="equation" v-html="html" :key="html">
	</span>
</template>

<style>
	.equation {
		zoom: 0.8;
	}

	span .MathJax {
		display: inline !important;
	}
	span svg {
		display: inline;
	}
</style>