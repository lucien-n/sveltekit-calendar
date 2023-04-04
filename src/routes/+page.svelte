<script lang="ts">
	import Calendar from '$lib/components/Calendar.svelte';
</script>

<div>
	<Calendar year={new Date().getFullYear()} month={new Date().getMonth()} />
</div>
