<script lang="ts">
	import Month from '$lib/components/Month.svelte';

	export let year: number;
	export let month: number;
</script>

<section id="calendar" class="h-full w-full">
	<Month {year} {month} />
</section>
