<script lang="ts">
	import Day from '$lib/components/Day.svelte';

	export let year: number;
	export let month: number;

	function daysInMonth(year: number, month: number) {
		return new Date(year, month, 0).getDate();
	}

	function getDays() {
		let days = [];
		for (let i = 0; i < daysInMonth(year, month); i++) {
			days.push(new Date(year, month, i));
		}
		console.log(days);
		return days;
	}

	let get_days = getDays();
</script>

<section id="month-{year}-{month}" class="grid">
	{#each get_days as date}
		<Day {date} />
	{/each}
</section>
