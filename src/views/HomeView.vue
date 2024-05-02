<template>
	<main class="tracker-wrapper">
		<Banner />

		<Balance
			:totalSavings="+totalSavings"
			:totalExpenses="+totalExpenses"
		/>

		<IncomeExpensesList :expenses="expenses" @itemDeleted="itemDeleted" />

		<Form @itemAdded="itemAdded" />
	</main>
</template>

<script setup>
import { ref, computed } from "vue";
import Banner from "../components/Banner.vue";
import Balance from "../components/Balance.vue";
import IncomeExpensesList from "../components/IncomeExpensesList.vue";
import Form from "../components/Form.vue";

const expenses = ref([
	{ id: 1, text: "cache 1", amount: 100 },
	{ id: 2, text: "cache 2", amount: 50 },
	{ id: 3, text: "cache 3", amount: 20 },
	{ id: 4, text: "cache 4", amount: -100 },
	{ id: 5, text: "cache 5", amount: -55 },
]);

const itemAdded = (obj) => {
	expenses.value.push({
		id: generateId(),
		text: obj.text,
		amount: obj.amount,
	});
};

const itemDeleted = (id) => {
	expenses.value = expenses.value.filter((val) => {
		return val.id != id;
	});
};

const generateId = () => {
	return Math.random().toString(36).substring(2);
};

const totalSavings = computed(() => {
	return expenses.value.reduce((total, expense) => {
		return total + expense.amount;
	}, 0);
});

const totalExpenses = computed(() => {
	return expenses.value
		.filter((val) => {
			return val.amount < 0;
		})
		.reduce((total, expense) => {
			return total + expense.amount;
		}, 0);
});
</script>
