<template>
	<div>
		<p>Books amount: {{ props.books.length }}</p>
		<!-- <p>Books price: {{ totalPrice2() }}</p> -->
		<p>Books price: {{ test }}</p>
	</div>
</template>
<script setup>
import { defineProps, computed } from "vue";
const props = defineProps({
	books: Array,
});

const test = computed({
	get() {
		return props.books.reduce((sum, prices) => {
			return (sum += prices.price);
		}, 0);
	},
});

/* function totalPrice2() {
	console.log("funkcja sie wykonala");

	return props.books.reduce((sum, prices) => {
		return (sum += prices.price);
	}, 0);
} */
</script>
