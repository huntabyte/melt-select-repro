<script lang="ts">
	import { createPopover, melt } from '@melt-ui/svelte';
	import { fade } from 'svelte/transition';

	const {
		elements: { content, trigger },
		states: { open }
	} = createPopover({
		forceVisible: true
	});
</script>

<button use:melt={$trigger}> Open popover </button>

{#if $open}
	<div
		use:melt={$content}
		transition:fade={{ duration: 200 }}
		class="border w-[300px] h-[300px] bg-black"
	>
		<slot />
	</div>
{/if}
