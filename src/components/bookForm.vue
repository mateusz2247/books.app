<template>
	<form @submit.prevent="submit(newBookTittle,newBookPrice)" >
		<label>
			Title:
			<input v-model="newBookTittle" type="text" name="title" />
       
		</label>
		<label>
			price:
			<input v-model="newBookPrice" type="number" name="price" />
		</label>
		<button>Add book </button>
	</form>
</template>

<script setup>

import { ref } from "vue";
import {defineEmits} from 'vue';
const emits = defineEmits(['submit'])

let newBookTittle = ref();
let newBookPrice = ref(0);

   
const submit=(newBookTittle,newBookPrice)=>{
    emits("submit",newBookTittle,newBookPrice);
    clear()
}

function clear(){
    newBookTittle= ''
    newBookPrice=''
}   

</script>
