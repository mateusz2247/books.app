<template>
    <div>
        <ul>
			<li :key="index" v-for="(book, index) in props.books">
				{{ book.title }},{{ book.price }}
				<button @click="props.removeBook(index)">Remove</button>
			</li>
		</ul>
    </div>

</template>

<script setup>
    import { defineProps} from "vue";
    const props = defineProps({
        books: Array,
        removeBook: Function
    })

</script>