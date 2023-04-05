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
		const days = [];
		const firstDay = new Date(year, month, 1);
		const lastDay = new Date(year, month + 1, 0);
		const offset = firstDay.getDay() - 1 || 6;

		for (let i = 1 - offset; i <= lastDay.getDate(); i++) {
			const date = new Date(year, month, i);
			const isInCurrentMonth = i > 0 && i <= lastDay.getDate();
			days.push({ date, isInCurrentMonth });
		}

		return days;
	}
</script>

<section id="month-{year}-{month}" class="h-full w-full">
	<div
		id="days-{year}-{month}"
		class="mx-auto grid w-full grid-flow-row grid-cols-7 gap-3 lg:w-2/3"
	>
		{#each daysOfTheWeek as day}
			<div class="rounded-md border p-2 shadow-md">
				<p class="text-center font-semibold">
					{day}
				</p>
			</div>
		{/each}
		{#each getDays() as day}
			<Day date={day.date} isInCurrentMonth={day.isInCurrentMonth} />
		{/each}
	</div>
</section>
