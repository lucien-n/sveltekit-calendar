<script lang="ts">
	import Calendar from '$lib/components/Calendar.svelte';
</script>

<div class="flex h-full w-full items-center">
	<Calendar year={new Date().getFullYear()} month={new Date().getMonth()} />
</div>
