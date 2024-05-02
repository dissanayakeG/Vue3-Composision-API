<template>
	<div class="income-expenses-list">
		<ul>
			<li
				class="plus item-wrapper"
				v-for="expense in expenses"
				:key="expense.id"
				:class="expense.amount < 0 ? 'minus' : 'plus'"
			>
				<span class="delete-button" @click="$emit('itemDeleted', expense.id)">X</span>
				<span class="text">Cache : $ {{ expense.amount }}</span>
			</li>
		</ul>
	</div>
</template>

<script setup>
const prop = defineProps({
	expenses: {
		type: Array,
		required: true,
	},
});
</script>
