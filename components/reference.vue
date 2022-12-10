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

<script>
	export default {
		props: ['number', 'authors', 'title', 'source', 'total']
	}
</script>
