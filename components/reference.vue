<script setup>
	import { defineProps } from 'vue'

	const props = defineProps({
		number: {
			type: Number,
			default: 0
		},
		authors: {
			type: String,
			default: ""
		},
		title: {
			type: String,
			default: ""
		},
		source: {
			type: String,
			default: ""
		},
		total: {
			type: Number,
			default: 0
		}
	})
</script>

<template>
	<div
		class="reference absolute bottom-2 text-sm font-100"
		:style="{ 'transform': `translate(0, ${number - total}00%)` }"
	>
		{{ `[${number}] ${authors}. ${title}. ${source}.` }}
	</div>
</template>

<style>
	.reference {
		font-family: "Times New Roman";
	}
</style>