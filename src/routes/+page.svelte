<script lang="ts">
	import Calendar from '$lib/components/Calendar.svelte';

	let year = 0;
	let month = 0;

	let dateInputValue: string = '1970-01-01';

	function refreshDate() {
		let date = new Date(dateInputValue);
		year = date.getFullYear();
		month = date.getMonth();
	}
</script>

<div class="h-full w-full">
	<div>
		<input type="date" bind:value={dateInputValue} on:input={refreshDate} />
	</div>
	<div class="flex items-center">
		<!-- Rerender component when date is updated -->
		{#key month | year}
			<Calendar {year} {month} />
		{/key}
	</div>
</div>
