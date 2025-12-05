<script lang="ts">
	import Button from '$lib/components/general/Button.svelte';
</script>

<div class="wrapper">
	<div class="showarea">
		<div class="row">
			<div class="col">
				<h1>Basic</h1>
				<Button type="primary">Primary</Button>
				<Button>Default</Button>
				<Button type="dashed">Dashed</Button>
				<Button type="text" block>Text</Button>
				<Button type="link" block>Link</Button>
			</div>
			<div class="col">
				<h1>Size</h1>
				<Button size="large">Large</Button>
				<Button size="medium">Medium</Button>
				<Button size="small">Small</Button>
			</div>
			<div class="col">
				<h1>Shape</h1>
				<Button>Rounded</Button>
				<Button shape="circle">Circle</Button>
			</div>
			<div class="col">
				<h1>Block</h1>
				<div>---------------</div>
				<Button block>Block</Button>
			</div>
			<div class="col">
				<h1>Danger</h1>
				<Button type="primary" danger>Primary</Button>
				<Button danger>Default</Button>
				<Button type="dashed" danger>Dashed</Button>
				<Button type="text" block danger>Text</Button>
				<Button type="link" block danger>Link</Button>
			</div>
			<div
				class="col"
				style="background-color: rgba(203, 203, 203, 1); padding: 0 1rem; padding-bottom: 1rem; border-radius: 6px;"
			>
				<h1>Ghost</h1>
				<Button type="primary" ghost>Primary</Button>
				<Button type="default" ghost>Default</Button>
				<Button type="dashed" ghost>Dashed</Button>
				<Button variant="solid" color="cyan" ghost>Cyan</Button>
				<Button variant="solid" color="purple" ghost>Purple</Button>
				<Button variant="solid" color="red" ghost>Text</Button>
				<Button variant="solid" color="pink" ghost>Pink</Button>
			</div>
			<div class="col">
				<h1>Disabled</h1>
				<Button type="primary" disabled>Primary</Button>
				<Button disabled>Default</Button>
				<Button type="dashed" disabled>Dashed</Button>
				<Button type="text" block disabled>Text</Button>
				<Button type="link" block disabled>Link</Button>
				<Button type="primary" block ghost disabled>Ghost</Button>
			</div>
			<div class="col">
				<h1>Loading</h1>
				<Button type="primary" loading>Primary</Button>
			</div>
		</div>
		<div class="row">
			<div class="col">
				<h1>Color & Variant</h1>
				<div class="row">
					<div class="col">
						<Button variant="solid" color="default">Solid</Button>
						<Button variant="solid" color="primary">Solid</Button>
						<Button variant="solid" color="danger">Solid</Button>
						<Button variant="solid" color="pink">Solid</Button>
						<Button variant="solid" color="purple">Solid</Button>
						<Button variant="solid" color="cyan">Solid</Button>
					</div>
					<div class="col">
						<Button variant="outlined" color="default">Outlined</Button>
						<Button variant="outlined" color="primary">Outlined</Button>
						<Button variant="outlined" color="danger">Outlined</Button>
						<Button variant="outlined" color="pink">Outlined</Button>
						<Button variant="outlined" color="purple">Outlined</Button>
						<Button variant="outlined" color="cyan">Outlined</Button>
					</div>
					<div class="col">
						<Button variant="dashed" color="default">Dashed</Button>
						<Button variant="dashed" color="primary">Dashed</Button>
						<Button variant="dashed" color="danger">Dashed</Button>
						<Button variant="dashed" color="pink">Dashed</Button>
						<Button variant="dashed" color="purple">Dashed</Button>
						<Button variant="dashed" color="cyan">Dashed</Button>
					</div>
					<div class="col">
						<Button variant="filled" color="default">Filled</Button>
						<Button variant="filled" color="primary">Filled</Button>
						<Button variant="filled" color="danger">Filled</Button>
						<Button variant="filled" color="pink">Filled</Button>
						<Button variant="filled" color="purple">Filled</Button>
						<Button variant="filled" color="cyan">Filled</Button>
					</div>
					<div class="col">
						<Button variant="text" color="default">Text</Button>
						<Button variant="text" color="primary">Text</Button>
						<Button variant="text" color="danger">Text</Button>
						<Button variant="text" color="pink">Text</Button>
						<Button variant="text" color="purple">Text</Button>
						<Button variant="text" color="cyan">Text</Button>
					</div>
					<div class="col">
						<Button variant="link" color="default">Link</Button>
						<Button variant="link" color="primary">Link</Button>
						<Button variant="link" color="danger">Link</Button>
						<Button variant="link" color="pink">Link</Button>
						<Button variant="link" color="purple">Link</Button>
						<Button variant="link" color="cyan">Link</Button>
					</div>
				</div>
			</div>
		</div>
		<div class="row">
			<div class="col">
				<h1>Type + Variant only</h1>
				<div class="row">
					<div class="col">
						<Button type="primary" variant="solid">Primary + Solid</Button>
						<Button type="primary" variant="outlined">Primary + Outlined</Button>
						<Button type="primary" variant="dashed">Primary + Dashed</Button>
						<Button type="primary" variant="filled">Primary + Filled</Button>
						<Button type="primary" variant="text">Primary + Text</Button>
						<Button type="primary" variant="link">Primary + Link</Button>
					</div>
					<div class="col">
						<Button type="default" variant="solid">Default + Solid</Button>
						<Button type="default" variant="outlined">Default + Outlined</Button>
						<Button type="default" variant="dashed">Default + Dashed</Button>
						<Button type="default" variant="filled">Default + Filled</Button>
						<Button type="default" variant="text">Default + Text</Button>
						<Button type="default" variant="link">Default + Link</Button>
					</div>
					<div class="col">
						<Button type="dashed" variant="solid">Dashed + Solid</Button>
						<Button type="dashed" variant="outlined">Dashed + Outlined</Button>
						<Button type="dashed" variant="dashed">Dashed + Dashed</Button>
						<Button type="dashed" variant="filled">Dashed + Filled</Button>
						<Button type="dashed" variant="text">Dashed + Text</Button>
						<Button type="dashed" variant="link">Dashed + Link</Button>
					</div>
					<div class="col">
						<Button type="text" variant="solid">Text + Solid</Button>
						<Button type="text" variant="outlined">Text + Outlined</Button>
						<Button type="text" variant="dashed">Text + Dashed</Button>
						<Button type="text" variant="filled">Text + Filled</Button>
						<Button type="text" variant="text">Text + Text</Button>
						<Button type="text" variant="link">Text + Link</Button>
					</div>
					<div class="col">
						<Button type="link" variant="solid">Link + Solid</Button>
						<Button type="link" variant="outlined">Link + Outlined</Button>
						<Button type="link" variant="dashed">Link + Dashed</Button>
						<Button type="link" variant="filled">Link + Filled</Button>
						<Button type="link" variant="text">Link + Text</Button>
						<Button type="link" variant="link">Link + Link</Button>
					</div>
				</div>
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
