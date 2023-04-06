<template>
	<form @submit.prevent="submit(newBookTittle, newBookPrice)">
		<label>
			Title:
			<input v-model="newBookTittle" type="text" name="title" />
		</label>
		<label>
			price:
			<input v-model="newBookPrice" type="number" name="price" />
		</label>
		<button>Add book</button>
	</form>

	<!-- <div>
		<h5>Products</h5>
		<ul>
			<li v-for="(product,index) in products" :key="index">{{ product.book.title }}</li>
		</ul>
	</div> -->
</template>

<script setup>
import { ref } from "vue";
import { defineEmits } from "vue";
const emits = defineEmits(["submit"]);

let newBookTittle = ref();
let newBookPrice = ref(0);

const submit = (newBookTittle2, newBookPrice2) => {
	emits("submit", newBookTittle2, newBookPrice2);
	newBookTittle.value = "";
	newBookPrice.value = "";
};

/* const products = ref(null);
fetch("https://api.itbook.store/1.0/new")
	.then((response) => response.json())
	.then((data) => (products.value = data));

console.log(products); */
</script>
