<template>
	<!-- <div>
        <ul>
			<li :key="index" v-for="(book, index) in props.books">
			TITLE:	{{ book.title }}, PRICE: {{ book.price }}
				<button @click="$emit('remove',index)">Remove</button>
			</li>
		</ul>
    </div> -->

 

	<v-list class="d-block bg-blue-darken-2" >
       
		<v-list-item class="text-center "
			v-for="(book, index) in props.books"
			:key="index"
			:title="'Title: ' + book.title + 'Price ' + book.price"
            
			:class="{
				'bg-red': parseInt(book.price.substring(1)) < 40,
                
			}">
            <v-btn 
            class="bg-white"
            small
            @click="$emit('remove',index)"
            prepend-icon="mdi-delete">Remove</v-btn>
            <v-divider></v-divider>
        </v-list-item>
 
 
	</v-list>


</template>

<script setup>
import { defineProps } from "vue";
const props = defineProps({
	books: Array,
});
</script>
