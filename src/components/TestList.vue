import { onMounted } from 'vue';
<template>
	<div ref="tableWrapper" class="list-container">
		<v-data-table
			:items="mockData"
			:headers="headers"
			disable-pagination
			hide-default-footer
		>
		</v-data-table>
	</div>
</template>

<script setup>
import { onMounted, ref } from 'vue';

const headers = [
	{ text: 'ID', value: 'id' },
	{ text: 'Name', value: 'name' },
	{ text: 'Description', value: 'description' },
];

const tableWrapper = ref(null);
const mockData = Array.from({ length: 500 }, (_, i) => ({
	id: i + 1,
	name: `Test ${i + 1}`,
	description: 'Description',
}));

onMounted(() => {
	// const table = tableWrapper.value.querySelector('.v-data-table');
});
</script>

<style scoped>
.list-container {
	height: 100%;
	max-height: 800px;
	overflow: auto;
}
</style>
