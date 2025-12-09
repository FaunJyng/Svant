<script module>
	import type { Snippet } from 'svelte';
	type Orientation = 'horizontal' | 'vertical';
	type Variant = 'dashed' | 'solid' | 'dotted';
	type Size = 'small' | 'medium' | 'large';
	type TitlePlacement = 'start' | 'center' | 'end';
	export type DividerProps = {
		children?: Snippet;
		plain?: boolean;
		horizontal?: boolean;
		vertical?: boolean;
		span?: boolean;
		orientation?: Orientation;
		dashed?: boolean;
		variant?: Variant;
		size?: Size;
		titlePlacement?: TitlePlacement;
	};
</script>

<script lang="ts">
	let {
		children = undefined,
		plain = false,
		vertical = undefined,
		span = false,
		orientation = 'horizontal',
		dashed = undefined,
		variant = 'solid',
		size = 'medium',
		titlePlacement = 'center',
	}: DividerProps = $props();
</script>

<div
	class={[
		'tokens',
		'root',
		`orientation-${orientation}`,
		`${span}`,
		`${vertical ? 'orientation-vertical' : undefined}`,
		`variant-${variant}`,
		`${dashed ? 'variant-dashed' : undefined}`,
		`title-placement-${titlePlacement}`,
		`size-${size}`,
	]}
>
	{#if children}
		<span class={['rail', 'first-rail']}></span>
		<span class={['content', { plain }]}>
			{@render children()}
		</span>
		<span class={['rail', 'second-rail']}></span>
	{:else}
		<span class={['rail', 'single-rail']}></span>
	{/if}
</div>

<style>
	/* Component tokens */
	.tokens {
		/* Root */
		--preset-div-root-width: 100%;
		--preset-div-root-height: fit-content;
		--preset-div-root-flex-direction: row;
		--preset-div-root-margin-block: var(--svant-margin-block);
		--preset-div-root-margin-inline: 0px;
		--preset-div-root-orientation-margin: 0.05;

		/* Content */
		--preset-div-content-padding-inline: 1em;
		--preset-div-content-writing-mode: unset;
		--preset-div-content-text-orientation: unset;
		--preset-div-content-text-color: var(--svant-text-color-general-theme);

		/* Rail */
		/* --preset-div-rail-color: var(--svant-seperator-color); */
		--preset-div-rail-color: blue;

		--preset-div-single-rail-line-width: var(--svant-line-width);
		--preset-div-single-rail-style: solid;
		--preset-div-single-rail-width: 100%;
		--preset-div-single-rail-height: 0px;

		--preset-div-first-rail-line-width: var(--svant-line-width);
		--preset-div-first-rail-style: solid;
		--preset-div-first-rail-width: 50%;
		--preset-div-first-rail-height: 0px;

		--preset-div-second-rail-line-width: var(--svant-line-width);
		--preset-div-second-rail-style: solid;
		--preset-div-second-rail-width: 50%;
		--preset-div-second-rail-height: 0px;
	}

	/* Rendered tokens */
	.tokens {
		/* Root */
		--div-root-width: var(--preset-div-root-width);
		--div-root-height: var(--preset-div-root-height);
		--div-root-flex-direction: var(--preset-div-root-flex-direction);
		--div-root-margin-block: var(--preset-div-root-margin-block);
		--div-root-margin-inline: var(--preset-div-root-margin-inline);

		/* Content */
		--div-content-writing-mode: var(--preset-div-content-writing-mode);
		--div-content-text-orientation: var(--preset-div-content-text-orientation);
		--div-content-font-size: var(--svant-font-size);
		--div-content-line-height: var(--svant-line-height-relative);
		--div-content-padding-inline: var(--preset-div-content-padding-inline);
		--div-content-text-color: var(--preset-div-content-text-color);

		/* Rail */
		--div-rail-color: var(--preset-div-rail-color);

		--div-single-rail-line-width: var(--preset-div-single-rail-line-width);
		--div-single-rail-style: var(--preset-div-single-rail-style);
		--div-single-rail-width: var(--preset-div-single-rail-width);
		--div-single-rail-height: var(--preset-div-single-rail-height);

		--div-first-rail-line-width: var(--preset-div-first-rail-line-width);
		--div-first-rail-style: var(--preset-div-first-rail-style);
		--div-first-rail-width: var(--preset-div-first-rail-width);
		--div-first-rail-height: var(--preset-div-first-rail-height);

		--div-second-rail-line-width: var(--preset-div-second-rail-line-width);
		--div-second-rail-style: var(--preset-div-second-rail-style);
		--div-second-rail-width: var(--preset-div-second-rail-width);
		--div-second-rail-height: var(--preset-div-second-rail-height);
	}

	/* Orientation layer */

	/* .orientation-horizontal {} */

	.orientation-vertical {
		--div-root-margin-block: 0px;
		--div-root-height: 1em;
		--div-root-width: 0px;

		--div-content-writing-mode: vertical-lr;
		--div-content-text-orientation: upright;
	}

	.span.orientation-vertical {
		--div-root-height: 100%;
	}

	/* Size layer */

	.orientation-horizontal.size-medium {
		--div-root-margin-block: var(--svant-margin-block);
	}

	.orientation-horizontal.size-small {
		--div-root-margin-block: var(--svant-margin-block-xs);
	}

	.orientation-horizontal.size-large {
		--div-root-margin-block: var(--svant-margin-block-lg);
	}

	.orientation-vertical.size-medium {
		--div-root-margin-inline: var(--svant-margin-inline);
	}

	.orientation-vertical.size-small {
		--div-root-margin-inline: var(--svant-margin-inline-xs);
	}

	.orientation-vertical.size-large {
		--div-root-margin-inline: var(--svant-margin-inline-lg);
	}

	/* Varient layer */
	.variant-dashed {
		--div-single-rail-style: dashed;
		--div-first-rail-style: dashed;
		--div-second-rail-style: dashed;
	}

	.variant-solid {
		--div-single-rail-style: solid;
		--div-first-rail-style: solid;
		--div-second-rail-style: solid;
	}

	.variant-dotted {
		--div-single-rail-style: dotted;
		--div-first-rail-style: dotted;
		--div-second-rail-style: dotted;
	}

	/* Root layer */
	.root {
		width: var(--div-root-width);
		height: var(--div-root-height);

		flex-direction: var(--div-root-flex-direction);

		margin: var(--div-root-margin-block) var(--div-root-margin-inline);
		display: flex;
		align-items: center;
	}

	.content {
		writing-mode: var(--div-content-writing-mode);
		text-orientation: var(--div-content-text-orientation);

		padding: 0 var(--div-content-padding-inline);

		font-size: var(--div-content-font-size);
		line-height: var(--div-content-font-size);
		font-weight: var(--svant-font-weight-semibold);

		color: var(--div-content-text-color);
	}

	.content.plain {
		font-weight: var(--svant-font-weight-regular);
	}

	.orientation-horizontal .single-rail {
		width: var(--svk-div-single-rail-width, var(--div-single-rail-width));
		height: var(--svk-div-single-rail-height, var(--div-single-rail-height));
		border-top-width: var(--svk-div-single-rail-line-width, var(--div-single-rail-line-width));
		border-top-style: var(--svk-div-single-rail-style, var(--div-single-rail-style));
		border-top-color: var(--svk-div-single-rail-color, var(--div-rail-color));
	}

	.orientation-horizontal .first-rail {
		width: var(--svk-div-first-rail-width, var(--div-first-rail-width));
		height: var(--svk-div-first-rail-height, var(--div-first-rail-height));
		border-top-width: var(--div-first-rail-line-width);
		border-top-style: var(--svk-div-first-rail-style, var(--div-first-rail-style));
		border-top-color: var(--svk-div-first-rail-color, var(--div-rail-color));
	}

	.orientation-horizontal .second-rail {
		line-height: var(--div-content-line-height);
		width: var(--svk-div-second-rail-width, var(--div-second-rail-width));
		height: var(--svk-div-second-rail-height, var(--div-second-rail-height));
		border-top-width: var(--svk-div-second-rail-line-width, var(--div-second-rail-line-width));
		border-top-style: var(--svk-div-second-rail-style, var(--div-second-rail-style));
		border-top-color: var(--svk-div-second-rail-color, var(--div-rail-color));
	}
</style>
