<script lang="ts">
	import { createEventDispatcher } from 'svelte';
	import { fade, slide } from 'svelte/transition';

	export let open = false;

	console.log(open);

	const closeDispatcher = createEventDispatcher();

	function handleClose() {
		closeDispatcher('close');
		open = false;
	}
</script>

{#if open}
	<!-- svelte-ignore a11y-no-static-element-interactions -->
	<div
		class="absolute h-full w-full top-0 left-0 bg-black opacity-60"
		transition:fade={{ duration: 150 }}
		on:click={handleClose}
		on:keypress
	/>
	<div
		class={`absolute left-0 bottom-12 rounded-t-3xl max-h-[90%] w-screen overflow-scroll ${$$props.class} bg-slate-300`}
		transition:slide={{ duration: 150, axis: 'y' }}
	>
		<slot />
	</div>
{/if}
