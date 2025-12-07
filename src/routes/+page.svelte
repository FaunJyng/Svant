<script lang="ts">
	import Button from '$lib/components/general/Button.svelte';
	import { AlertFilled } from '@axolt/svicon-ant';
	let loading = $state(false);
</script>

<div class="wrapper">
	<div class="showarea"></div>
</div>

<style>
	.wrapper {
		width: 100%;
		min-height: 100vh;
		padding: 5rem 0;
		display: flex;
		justify-content: center;
		align-items: center;
	}

	.showarea {
		display: flex;
		align-items: flex-start;
		flex-direction: column;
		row-gap: 1rem;
	}

	.row {
		display: flex;
		column-gap: 14px;
	}

	.col {
		display: flex;
		flex-direction: column;
		row-gap: 8px;
		align-items: flex-start;
	}
</style>
