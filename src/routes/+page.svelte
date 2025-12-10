<script lang="ts">
	import Button from '$lib/components/general/Button.svelte';
	import Divider from '$lib/components/layout/Divider.svelte';
	let contentPlacement = $state('end');
</script>

<div class="wrapper">
	<div class="showarea">
		<div class="row">
			<div class="col" style="width: 500px;">
				<Button
					label="Click"
					onclick={() => {
						contentPlacement = 'start';
					}}
				/>
				<div>----------------------------------------------</div>
				<Divider {contentPlacement} size="medium">Divider</Divider>
				Et est sea justo amet voluptua aliquyam et amet sed. Magna diam rebum sadipscing ut est.
				Et ut dolor stet.
				<div style="display: flex;">
					<Divider contentPlacement="center" size="small" vertical>DIV</Divider>
					<Divider vertical span dashed />
				</div>
				<div style="display: flex;">
					Text <Divider vertical />
				</div>
				Kasd erat stet dolor sit ipsum amet. Dolore magna magna kasd est at justo voluptua, lorem
				eirmod dolor diam ea.
				<Divider contentPlacement="end" />
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
