<script setup>
	import { defineProps } from 'vue'

	const props = defineProps({
		type: {
			type: String,
			default: ""
		},
		name: {
			type: String,
			default: ""
		},
		number: {
			type: Number,
			default: 0
		}
	})
</script>


<template>
	<div class="theorem my-1 p-2 border-1 border-black text-lg bg-white" :name="name" :number="number">
		<b>{{ type ? type : "Theorem" }}{{ number ? ` ${number}` : '' }}</b><span>{{ name ? ` (${name})` : '' }}</span><b>.</b><i><slot></slot></i>
	</div>
</template>

<style>
@font-face {
	font-family: 'Lartin Modern';
	src: url('../public/fonts/lmroman10-italic.otf') format('opentype');
	font-style: italic;
	font-weight: normal;
}
@font-face {
	font-family: 'Lartin Modern';
	src: url('../public/fonts/lmroman10-regular.otf') format('opentype');
	font-style: normal;
	font-weight: normal;
}
@font-face {
	font-family: 'Lartin Modern';
	src: url('../public/fonts/lmroman10-bold.otf') format('opentype');
	font-style: bold;
	font-weight: bold;
}
@font-face {
	font-family: 'Lartin Modern';
	src: url('../public/fonts/lmroman10-bolditalic.otf') format('opentype');
	font-style: italic;
	font-weight: bold;
}
.theorem {
	font-family: 'Lartin Modern';
	line-height: 1.1em;
}
</style>
