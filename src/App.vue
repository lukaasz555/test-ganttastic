<template>
	<v-app>
		<v-main>
			<div class="wrapper">
				<TestChart />
				<TestList />
			</div>
		</v-main>
	</v-app>
</template>

<script setup>
import { onMounted, ref } from 'vue';
import TestChart from './components/TestChart.vue';
import TestList from './components/TestList.vue';

const text = ref('');

onMounted(() => {
	text.value = 'text';
});
</script>

<style scoped>
.wrapper {
	max-width: 1200px;
	max-height: 700px;
	margin: 4em auto 2em;
	display: grid;
	gap: 10px;
	grid-template-columns: 1fr 300px;
}
</style>
