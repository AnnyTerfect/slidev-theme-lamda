<template>
	<div class="theorem my-1 p-2 border-1 border-black text-xl" :class="class" :name="name" :number="number">
		<b>{{ type ? type : "Theorem" }}{{ number ? ` ${number}` : '' }}</b>{{ name ? ` (${name})` : '' }}<b>.</b>&nbsp;&nbsp;<i><slot></slot></i>
	</div>
</template>

<style>
.theorem {
	font-family: "Times New Roman";
	line-height: 1.1em;
}
</style>

<script>
	export default {
		props: ['type', 'class', 'name', 'number']
	}
</script>
