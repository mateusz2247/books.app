<template>
	<div id="app">
		<!-- heading -->
		<header>
			<h1>Books<span>.app</span></h1>
		</header>

		<!-- books list -->
		<booksList @remove="removeBook" :books="books" />

		<!-- no books message -->
		<booksLengthMsg :books="books" />

		<!-- add book form -->
		<bookForm @submit="addBook" />

		<booksSummary :books="books" />

		<!-- <li v-show="!products"  v-for="(product, index) in products" :key="index"></li> -->
	</div>
</template>

<script setup>
import { reactive, ref } from "vue";
import booksList from "./components/booksList.vue";
import booksLengthMsg from "./components/booksLengthMsg.vue";
import bookForm from "./components/bookForm.vue";
import booksSummary from "./components/booksSummary.vue";

let books = reactive([
/* 	{
		title: " The catcher in the rye",
		price: 20,
	},
	{
		title: "Of mice and Men",
		price: 18,
	}, */
]);

function removeBook(index) {
	console.log(books);
	books.splice(index, 1);

}
function addBook(title, price) {
	let book = {
		title: title,
		price: '$'+price,
	};

	console.log("dodaje ksiazke");
	books.push(book);
	console.log(products);
	console.log(products.value)

}
const products = ref(null);

/* onMounted(() => { */
fetch("https://api.itbook.store/1.0/new")
	.then((response) => response.json())
	.then((data) => {
		products.value = data.books;
		books.push(products.value[0])
		books.push(products.value[1])
		books.push(products.value[2])
	});
	
</script>

<style>
#app {
	font-family: Avenir, Helvetica, Arial, sans-serif;
	-webkit-font-smoothing: antialiased;
	-moz-osx-font-smoothing: grayscale;
	text-align: center;
	color: #2c3e50;
	margin-top: 60px;
}
</style>
