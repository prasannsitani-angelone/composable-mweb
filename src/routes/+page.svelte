<script>
	import { Bottomsheet, CallbackCard } from 'composable-component-sdk';
	import { goto } from '$app/navigation';

	let open = false;

	function handleOverlayOpen() {
		open = true;
	}

	function handleOverlayClose() {
		open = false;
	}

	function handleExternalScreen() {
		// goto('/about');
		goto('http://localhost:3000/about');
	}

	let array = new Array();

	for (let i = 0; i < 20; i++) {
		array.push({ id: i, title: `Item ${i}` });
	}
</script>

<main>
	<div class="relative flex flex-col items-center gap-4 p-4 shadow-lg">
		{#each array as item}
			<CallbackCard
				on:external-overlay={handleOverlayOpen}
				on:external-screen={handleExternalScreen}
			/>
		{/each}
		<Bottomsheet {open} on:close={handleOverlayClose} />
	</div>
</main>

<style lang="postcss">
	:global(html) {
		background-color: theme(colors.gray.200);
	}
</style>
