<template>
	<v-app id="inspire"
	class="bg-blue"
	>
		<v-app-bar
			color="teal-darken-4"
			image="https://picsum.photos/1920/1080?random">
			<v-toolbar-title>Books.App</v-toolbar-title>
		</v-app-bar>

		<v-main>
			<div id="app">
				<bookForm @submit="addBook" />
				<booksList @remove="removeBook" :books="books" />

				<booksLengthMsg :books="books" />

				<booksSummary :books="books" />
			</div>
		</v-main>
	</v-app>
</template>

<script setup>
import { reactive, ref } from "vue";
import booksList from "./components/booksList.vue";
import booksLengthMsg from "./components/booksLengthMsg.vue";
import bookForm from "./components/bookForm.vue";
import booksSummary from "./components/booksSummary.vue";

let books = reactive([]);

function removeBook(index) {
	console.log(books);
	books.splice(index, 1);
}
function addBook(title, price) {
	let book = {
		title: title,
		price: "$" + price,
	};

	console.log("dodaje ksiazke");
	books.push(book);
	console.log(products);
	console.log(products.value);
}
const products = ref(null);

fetch("https://api.itbook.store/1.0/new")
	.then((response) => response.json())
	.then((data) => {
		books.push(...data.books.splice(0, 3));
	});

/* fetch("https://api.itbook.store/1.0/new")
	.then((response) => response.json())
	.then((data) => {
		products.value = data.books;
		books.push(products.value[0]);
		books.push(products.value[1]);
		books.push(products.value[2]);
	}); */
</script>
