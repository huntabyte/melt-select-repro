<script lang="ts">
	import { createSelect, melt } from '@melt-ui/svelte';

	// eslint-disable-next-line @typescript-eslint/no-explicit-any
	export let transit: any = undefined;

	// eslint-disable-next-line @typescript-eslint/no-unused-vars
	function someAction(node: HTMLElement) {
		return {
			destroy() {
				console.log('destroyed');
			}
		};
	}

	const {
		elements: { menu, option, trigger },
		states: { open }
	} = createSelect({
		forceVisible: true
	});

	const options = [
		{
			value: 'item-1',
			label: 'Is it accessible?'
		},
		{
			value: 'item-2',
			label: 'Is it unstyled?'
		},
		{
			value: 'item-3',
			label: 'Can it be animated?'
		}
	];
</script>

<button use:melt={$trigger}>Open Select</button>

{#if $open && transit}
	<div
		class="mx-auto w-full max-w-md rounded-md shadow-lg"
		use:melt={$menu}
		use:someAction
		transition:transit
	>
		{#each options as { label, value }}
			<div use:melt={$option({ label, value })}>{label}</div>
		{/each}
	</div>
{:else if $open}
	<div class="mx-auto w-full max-w-md rounded-md shadow-lg" use:melt={$menu} use:someAction>
		{#each options as { label, value }}
			<div use:melt={$option({ label, value })}>{label}</div>
		{/each}
	</div>
{/if}
