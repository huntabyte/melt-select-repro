<script lang="ts">
	import { fade } from 'svelte/transition';
	import Popover from './Popover.svelte';
	import Select from './Select.svelte';
</script>

<Popover>
	<Select transit={fade} />
</Popover>
