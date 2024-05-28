import { onMounted } from 'vue';
<template>
	<div class="chart-container">
		<g-gantt-chart
			:chart-start="chartData.myChartStart"
			:chart-end="chartData.myChartEnd"
			style="width: 2000px"
		>
			<g-gantt-row
				v-for="row in chartData.rows"
				:key="row.label"
				:label="row.label"
				:bars="row.bars"
				bar-start="myStart"
				bar-end="myEnd"
				label-width="40"
			>
				<template #bar-label="{ bar }">
					<div class="bar d-flex align-center justify-space-around">
						<div>
							{{ bar.myStart.split(' ')[1] }} - {{ bar.myEnd.split(' ')[1] }}
						</div>
						<div class="ml-2">// {{ bar.text }}</div>
						<div style="width: 20px; height: 20px">
							<v-img :src="logo" />
						</div>
					</div>
				</template>
			</g-gantt-row>
		</g-gantt-chart>
	</div>
</template>

<script setup>
import { GGanttChart, GGanttRow } from 'vue-ganttastic';
import logo from '../assets/logo.png';

const bars1 = [
	{
		myStart: '2020-03-01 06:00',
		myEnd: '2020-03-01 08:00',
		text: 'text1',
	},
	{
		myStart: '2020-03-01 09:00',
		myEnd: '2020-03-01 11:00',
		text: 'text1',
	},
	{
		myStart: '2020-03-01 12:00',
		myEnd: '2020-03-01 14:00',
		text: 'text1',
	},
	{
		myStart: '2020-03-01 15:00',
		myEnd: '2020-03-01 17:00',
		text: 'text1',
	},
	{
		myStart: '2020-03-01 18:00',
		myEnd: '2020-03-01 19:30',
		text: 'text1',
	},
	{
		myStart: '2020-03-01 20:00',
		myEnd: '2020-03-01 21:30',
		text: 'text1',
	},
];

const bars2 = [
	{
		myStart: '2020-03-01 07:00',
		myEnd: '2020-03-01 09:00',
		text: 'text2',
	},
	{
		myStart: '2020-03-01 10:00',
		myEnd: '2020-03-01 12:00',
		text: 'text2',
	},
	{
		myStart: '2020-03-01 13:00',
		myEnd: '2020-03-01 15:00',
		text: 'text2',
	},
	{
		myStart: '2020-03-01 16:00',
		myEnd: '2020-03-01 18:30',
		text: 'text2',
	},
	{
		myStart: '2020-03-01 20:00',
		myEnd: '2020-03-01 20:45',
		text: 'text2',
	},
	{
		myStart: '2020-03-01 21:00',
		myEnd: '2020-03-01 21:45',
		text: 'text2',
	},
];

const chartData = {
	myChartStart: '2020-03-01 06:00',
	myChartEnd: '2020-03-01 22:00',
	rows: Array.from({ length: 700 }, (_, i) => ({
		id: i + 1,
		label: `row #${i + 1}`,
		bars: i % 2 === 0 ? bars1 : bars2,
	})),
};
</script>

<style scoped>
.chart-container {
	max-width: 900px;
	max-height: 800px;
	overflow-y: auto;
	overflow-x: auto;
	padding-bottom: 20px;
}

.bar {
	width: 100%;
	height: 100%;
}

.g-gantt-bar-label {
	border: 1px solid red;
	padding: 0;
}
</style>
