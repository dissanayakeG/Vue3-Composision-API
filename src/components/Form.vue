<template>
	<form class="form" @submit.prevent="submitForm">
		<div class="input-element">
			<label> Text:</label>
			<input type="text" v-model="text" />
		</div>
		<div class="input-element">
			<label> Amount: </label>
			<input type="text" v-model="amount" />
		</div>

		<button class="submit-btn">Submit</button>
	</form>
</template>

<script setup>
import { ref } from "vue";
const text = ref("");
const amount = ref("");

const emits = defineEmits(["itemAdded"]);

const submitForm = () => {
	if (!text.value || !amount.value) {
		alert("Empty values cannot be submitted!");
		return;
	}

	emits("itemAdded", {
		text: text.value,
		amount: amount.value,
	});

	text.value = "";
	amount.value = "";
};
</script>
