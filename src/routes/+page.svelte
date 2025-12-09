<script lang="ts">
	import Divider from '$lib/components/layout/Divider.svelte';
	import { Button } from '$lib/index.js';
	let content = $state('如需继续');
	let loading = $state(false);
</script>

<div class="wrapper">
	<div class="showarea">
		<div class="row">
			<div class="col">
				<div>----------------------------------------------</div>
				<Divider plain>Divider</Divider>
				<Button
					type="primary"
					label={content}
					{loading}
					onclick={() => {
						loading = true;
						setTimeout(() => {
							loading = false;
						}, 2000);
					}}
				/>
				<Divider />
			</div>
		</div>
	</div>
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
