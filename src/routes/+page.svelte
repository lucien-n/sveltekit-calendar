<script lang="ts">
	import Calendar from '$lib/components/Calendar.svelte';
</script>

<div class="h-full w-full">
	<Calendar year={new Date().getFullYear()} month={new Date().getMonth()} />
</div>
