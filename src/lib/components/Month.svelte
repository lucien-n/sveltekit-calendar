<script lang="ts">
	import Day from '$lib/components/Day.svelte';

	export let year: number;
	export let month: number;

	let daysOfTheWeek = [
		'Monday',
		'Tuesday',
		'Wednesday',
		'Thursday',
		'Friday',
		'Saturday',
		'Sunday'
	];

	function daysInMonth(year: number, month: number) {
		return new Date(year, month, 0).getDate();
	}

	function getMonday(year: number, month: number) {
		let date = new Date(year, month, 0);
		let day = date.getDay();
		let diff = date.getDate() - day + (day == 0 ? -6 : 1);
		return new Date(date.setDate(diff));
	}

	function getDays() {
		let days = [];
		let monday = getMonday(year, month);
		for (let i = 0; i < daysInMonth(year, monday.getMonth()) - monday.getDay(); i++) {
			days.push(new Date(year, monday.getMonth(), i));
		}
		for (let i = 0; i < daysInMonth(year, month); i++) {
			days.push(new Date(year, month, i));
		}
		return days;
	}
</script>

<section id="month-{year}-{month}" class="grid grid-flow-row grid-cols-7">
	{#each daysOfTheWeek as day}
		<div>
			{day}
		</div>
	{/each}
	{#each getDays() as date}
		<Day {date} />
	{/each}
</section>
