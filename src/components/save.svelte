<script>
	import { current_data, saveData, saved_spinner } from '$lib/index.js';
	import { faFloppyDisk, faSpinner } from '@fortawesome/free-solid-svg-icons';
	import Fa from 'svelte-fa';
</script>

<button
	type="submit"
	class="bg-sky-400 px-3 py-2 rounded-md cursor-pointer flex gap-2 items-center justify-center"
	on:click={() => {
		saveData($current_data);
	}}
>
	<Fa icon={faFloppyDisk} />
	Save
	{#if $saved_spinner}
		<Fa icon={faSpinner} class="animate-spin" />
	{/if}
</button>
