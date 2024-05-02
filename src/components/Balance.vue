<template>
	<div class="balance">
		<div class="saving">Total Savings : $ {{ totalSavings }}</div>
		<div class="divider"></div>
		<div class="expenses">Total Expenses: -$ {{ totalExpenses }}</div>
	</div>
</template>

<script setup>
const props = defineProps({
	totalSavings: { type: Number },
	totalExpenses: { type: Number },
});
</script>
