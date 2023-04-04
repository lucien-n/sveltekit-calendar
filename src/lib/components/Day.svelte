<script lang="ts">
	export let date: Date;
</script>

<div id="day-{date.getDay()}">
	{date.getDate()}
</div>
