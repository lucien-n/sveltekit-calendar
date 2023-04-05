<script lang="ts">
	import Month from '$lib/components/Month.svelte';

	export let year: number;
	export let month: number;
</script>

<section id="calendar" class="mx-auto h-4/5 w-4/5">
	<Month {year} {month} />
</section>
