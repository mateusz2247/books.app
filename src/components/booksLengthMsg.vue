<template>
	<v-card class="bg-purple-lighten-2 text-center"> 
	<div>
		<p v-show="!props.books.length">Go get some books!</p>
		<p v-show="props.books.length > 5">{{ props.books.length }} books</p>
		<p v-show="props.books.length <= 5 && props.books.length > 1">
			Not too many of them..
		</p>
		<p v-show="props.books.length == 1">One single book!</p>
	</div>
</v-card>
</template>

<script setup>
import { defineProps } from "vue";
const props = defineProps({
	books: Array,
});
</script>
