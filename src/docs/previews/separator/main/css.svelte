<script lang="ts">
	import { createSeparator, type CreateSeparatorProps } from '@melt-ui/svelte';

	export let orientation: CreateSeparatorProps['orientation'] = 'vertical';

	const { root: vertical } = createSeparator({
		orientation,
	});

	const { root: horizontalSeparator } = createSeparator({
		orientation: 'horizontal',
		decorative: true,
	});

	const icecreams = ['Caramel', 'Vanilla', 'Napolitan'];
</script>

<h2>Melt UI</h2>
<p>Flavors for everyone</p>
<div {...$horizontalSeparator} class="separator separator--horizontal" />
<div class="ice-creams">
	{#each icecreams as icecream, i}
		<p>{icecream}</p>
		{#if i !== icecreams.length - 1}
			<div {...$vertical} class="separator separator--vertical" />
		{/if}
	{/each}
</div>

<style lang="postcss">
	h2 {
		font-weight: var(--tw-font-weight-bold);
	}

	.ice-creams {
		display: flex;
		align-items: center;
		column-gap: var(--tw-size-3_5);
	}

	.separator {
		--tw-bg-opacity: 1;

		background-color: rgb(255 255 255 / var(--tw-bg-opacity));
	}

	.separator--horizontal {
		margin-top: var(--tw-size-3_5);
		margin-bottom: var(--tw-size-3_5);
		height: 1px;
		width: 100%;
	}

	.separator--vertical {
		height: var(--tw-size-4);
		width: 1px;
	}
</style>
