<script lang="ts">
	export let date: Date;
	export let isInCurrentMonth: boolean;
</script>

<div
	id="day-{date.getDay()}"
	class="w-1/7 aspect-square rounded-md border border-zinc-100 p-1 shadow-md transition-all duration-200 ease-in-out hover:cursor-pointer hover:border-zinc-400"
	class:opacity-50={!isInCurrentMonth}
>
	{date.getDate()}
</div>
