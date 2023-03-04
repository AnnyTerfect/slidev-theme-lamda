<script setup>
	import "mathjax-full/es5/tex-svg-full";
	import { defineProps, computed, useSlots } from 'vue'

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

<style>
	.equation > svg{
		margin: auto;
	}
</style>

<template>
	<div class="equation" :style="{ fontSize: fontSize }" v-html="html" :key="html">
	</div>
</template>