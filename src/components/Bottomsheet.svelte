<script lang="ts">
	import { createEventDispatcher } from 'svelte';
	import { fade, slide } from 'svelte/transition';

	export let open = false;

	const closeDispatcher = createEventDispatcher();

	function handleClose() {
		// document.body.style.overflow = 'auto';
		closeDispatcher('close');
	}
</script>

{#if open}
	<!-- svelte-ignore a11y-no-static-element-interactions -->
	<!-- <div
		class="absolute h-full w-full top-0 left-0 bg-black opacity-60 overflow-hidden"
		transition:fade={{ duration: 150 }}
		on:click={handleClose}
		on:keypress
	/> -->
	<div
		class="fixed inset-0 bg-black opacity-50 z-50"
		transition:fade={{ duration: 150 }}
		on:click={handleClose}
		on:keypress
	/>
	<div
		class={`fixed left-0 bottom-0 rounded-t-3xl max-h-[90%] w-screen ${$$props.class} bg-white z-50`}
		transition:slide={{ duration: 150, axis: 'y' }}
	>
		<div class="p-6">
			<div class="flex flex-col gap-4 justify-center items-center">
				<h2 class="bold text-xl">Bottom Sheet Height</h2>
				<p class="text-gray-600 text-ellipsis">
					Lorem ipsum dolor, sit amet consectetur adipisicing elit. Est voluptate reiciendis
					perspiciatis, suscipit fugit expedita qui, doloribus quo iusto officia deserunt nam
					voluptates porro. Sed pariatur nemo sequi minima adipisci?
				</p>
				<button class="btn btn-primary w-40" on:click={handleClose}> Close </button>
			</div>
		</div>
		<slot />
	</div>
{/if}
