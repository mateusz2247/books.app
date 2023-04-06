<template>
    <div>
        <ul>
			<li :key="index" v-for="(book, index) in props.books">
				{{ book.title }},{{ book.price }}
				<button @click="$emit('remove',index)">Remove</button>
			</li>
		</ul>
    </div>

</template>

<script setup>
    import { defineProps } from "vue";
    const props = defineProps({
        books: Array
    })

</script>