<script module>
	import type { AutoComplete } from '$lib/utils/helper-types.js';
	import type { Snippet } from 'svelte';
	type Orientation = AutoComplete<'horizontal' | 'vertical'>;
	type Variant = AutoComplete<'dashed' | 'solid' | 'dotted'>;
	type Size = AutoComplete<'small' | 'medium' | 'large'>;
	type ContentPlacement = AutoComplete<'start' | 'center' | 'end'>;
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
		contentPlacement?: ContentPlacement;
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
		contentPlacement = 'center',
	}: DividerProps = $props();
</script>

<span
	class={[
		'tokens',
		`orientation-${vertical ? 'vertical' : orientation}`,
		`${span ? 'span' : undefined}`,
		`size-${size}`,
		`variant-${dashed ? 'dashed' : variant}`,
		`content-placement-${contentPlacement}`,
		'root',
	]}
>
	{#if children}
		<span class={['first-rail', 'rail']}></span>
		<span class={[{ plain }, 'content']}>
			{@render children?.()}
		</span>
		<span class={['second-rail', 'rail']}></span>
	{:else}
		<span class={['single-rail', 'rail']}></span>
	{/if}
</span>

<style>
	/* Component tokens */
	.tokens {
		/* Root */
		--div-root-flex-direction: row;
		--div-root-width: 100%;
		--div-root-height: auto;
		--div-root-margin-block: var(--svant-margin-block);
		--div-root-margin-inline: 0px;

		/* Content */
		--div-content-padding-inline: 1em;
		--div-content-padding-block: 0px;
		--div-content-writing-mode: unset;
		--div-content-text-orientation: unset;
		--div-content-font-weight: 700;
		--div-content-text-color: var(--svant-text-color-general-theme);

		/* Rail */
		--div-rail-content-placement-margin-factor: 0.1;

		--div-rail-line-color: var(--svant-seperator-color);

		--div-single-rail-length: 100%;
		--div-single-rail-line-width: var(--svant-line-width);
		--div-single-rail-line-style: solid;

		--div-first-rail-length: 50%;
		--div-first-rail-line-width: var(--svant-line-width);
		--div-first-rail-line-style: solid;

		--div-second-rail-length: 50%;
		--div-second-rail-line-width: var(--svant-line-width);
		--div-second-rail-line-style: solid;
	}

	/* Orientation layer */
	.orientation-vertical {
		--div-root-flex-direction: column;
		--div-root-width: max-content;
		--div-root-margin-block: 0px;

		--div-content-padding-inline: 0px;
		--div-content-writing-mode: vertical-lr;
		--div-content-text-orientation: upright;

		--div-single-rail-length: 1em;
		--div-first-rail-length: 1em;
		--div-second-rail-length: 1em;
	}

	.orientation-vertical.span {
		--div-single-rail-length: 100%;
		--div-first-rail-length: 50%;
		--div-second-rail-length: 50%;
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

	/* Variant layer */
	.variant-dashed {
		--div-single-rail-line-style: dashed;
		--div-first-rail-line-style: dashed;
		--div-second-rail-line-style: dashed;
	}

	.variant-dotted {
		--div-single-rail-line-style: dotted;
		--div-first-rail-line-style: dotted;
		--div-second-rail-line-style: dotted;
	}

	/* Content placement layer */
	.content-placement-start {
		--div-first-rail-length: calc(100% * var(--div-rail-content-placement-margin-factor));
		--div-second-rail-length: calc(100% * (1 - var(--div-rail-content-placement-margin-factor)));
	}

	.content-placement-center {
		--div-first-rail-length: 50%;
		--div-second-rail-length: 50%;
	}

	.content-placement-end {
		--div-first-rail-length: calc(100% * (1 - var(--div-rail-content-placement-margin-factor)));
		--div-second-rail-length: calc(100% * var(--div-rail-content-placement-margin-factor));
	}

	.orientation-vertical.content-placement-start:not(.span) {
		--div-first-rail-length: calc(1em * var(--div-rail-content-placement-margin-factor));
		--div-second-rail-length: calc(1em * (1 - var(--div-rail-content-placement-margin-factor)));
	}

	.orientation-vertical.content-placement-center:not(.span) {
		--div-first-rail-length: 1em;
		--div-second-rail-length: 1em;
	}

	.orientation-vertical.content-placement-end:not(.span) {
		--div-first-rail-length: calc(1em * (1 - var(--div-rail-content-placement-margin-factor)));
		--div-second-rail-length: calc(1em * var(--div-rail-content-placement-margin-factor));
	}

	/* Plain layer */
	.plain {
		--div-content-font-weight: 400;
	}

	/* Root */
	.root {
		display: flex;
		flex-direction: var(--div-root-flex-direction);
		justify-content: center;
		align-items: center;

		width: var(--div-root-width);
		height: var(--div-root-height);

		margin: var(--div-root-margin-block) var(--div-root-margin-inline);
	}

	/* Content */
	.content {
		padding: var(--div-content-padding-block) var(--div-content-padding-inline);
		writing-mode: var(--div-content-writing-mode);
		text-orientation: var(--div-content-text-orientation);
		color: var(--div-content-text-color);
		font-weight: var(--div-content-font-weight);
	}

	/* Rail */
	.single-rail,
	.first-rail,
	.second-rail {
		display: flex;
		align-items: center;
		justify-content: center;
		transition: width var(--svant-motion-duration-slow) var(--svant-motion-ease-in-out);
	}

	.orientation-horizontal .single-rail {
		width: var(--div-single-rail-length);
	}

	.orientation-horizontal .single-rail::before {
		content: '';
		width: 100%;
		border-top: var(--div-single-rail-line-width) var(--div-single-rail-line-style)
			var(--div-rail-line-color);
	}

	.orientation-horizontal .first-rail {
		width: var(--div-first-rail-length);
	}

	.orientation-horizontal .first-rail::before {
		content: '';
		width: 100%;
		border-top: var(--div-first-rail-line-width) var(--div-first-rail-line-style)
			var(--div-rail-line-color);
	}

	.orientation-horizontal .second-rail {
		width: var(--div-second-rail-length);
	}

	.orientation-horizontal .second-rail::before {
		content: '';
		width: 100%;
		border-top: var(--div-second-rail-line-width) var(--div-second-rail-line-style)
			var(--div-rail-line-color);
	}

	.orientation-vertical .single-rail {
		height: var(--div-single-rail-length);
	}

	.orientation-vertical .single-rail::before {
		content: '';
		height: 100%;
		border-right: var(--div-single-rail-line-width) var(--div-single-rail-line-style)
			var(--div-rail-line-color);
	}

	.orientation-vertical .first-rail {
		height: var(--div-first-rail-length);
	}

	.orientation-vertical .first-rail::before {
		content: '';
		height: 100%;
		border-right: var(--div-first-rail-line-width) var(--div-first-rail-line-style)
			var(--div-rail-line-color);
	}

	.orientation-vertical .second-rail {
		height: var(--div-second-rail-length);
	}

	.orientation-vertical .second-rail::before {
		content: '';
		height: 100%;
		border-right: var(--div-second-rail-line-width) var(--div-second-rail-line-style)
			var(--div-rail-line-color);
	}
</style>
