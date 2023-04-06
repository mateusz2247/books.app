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
			let test = prices.price.substring(1)
			
			return (sum += parseInt(test));
		}, 0);
	},
});


</script>
