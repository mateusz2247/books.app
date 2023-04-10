<template>
	<!-- <form @submit.prevent="submit(newBookTittle, newBookPrice)">
		<label>
			Title:
			<input v-model="newBookTittle" type="text" name="title" />
		</label>
		<label>
			price:
			<input v-model="newBookPrice" type="number" name="price" />
		</label>
		<button>Add book</button>
	</form> -->

	<v-sheet  width="300" class="mx-auto bg-blue">
		<v-form @submit.prevent="submit(newBookTittle, newBookPrice)">
			<v-text-field
				v-model="newBookTittle"
				label="Nazwka skiazki"
				type="text"></v-text-field>
			<v-text-field
				v-model="newBookPrice"
				label="Cena kiazki"
				
				type="number"></v-text-field>
			<v-btn  type="submit" block class="mt-2 bg-white">Dodaj ksiazke</v-btn>
		</v-form>
	</v-sheet>
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
</script>
