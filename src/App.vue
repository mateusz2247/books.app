<template>
	<div id="app">
		<!-- heading -->
		<header>
			<h1>Books<span>.app</span></h1>
		</header>

		<!-- books list -->
		<booksList 
    :removeBook="removeBook"
    :books="books" />

		<!-- no books message -->
		<p v-show="!books.length">Go get some books!</p>
		<p v-show="books.length > 5">{{ books.length }} ksiazek</p>
		<p v-show="books.length <= 5 && books.length > 1">Not too many of them..</p>
		<p v-show="books.length == 1">One single book!</p>

		<!-- add book form -->
		<form @submit.prevent="addBook">
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
	</div>
</template>

<script setup>
import { ref, reactive } from "vue";
import booksList from "./components/booksList.vue"

let newBookTittle = ref();
let newBookPrice = ref(0);

const books = reactive([
	{
		title: " The catcher in the rye",
		price: 20,
	},
	{
		title: "Of mice and Men",
		price: 18,
	},
]);

function removeBook(index) {
	console.log(index);
	this.books.splice(index, 1);
}
function addBook() {
	let newBook = {
		title: newBookTittle.value,
		price: newBookPrice.value,
	};
	console.log("dodaje ksiazke");
	books.push(newBook);
	newBookTittle.value = "";
	newBookPrice.value = 0;
}
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
