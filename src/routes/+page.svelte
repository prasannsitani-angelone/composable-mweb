<script>
	import { CallbackCard } from 'composable-component-sdk';
	import Carousel from '../components/Carousel.svelte';
	// import Card from '../components/Card.svelte';
	import Bottomsheet from '../components/Bottomsheet.svelte';

	let open = false;

	function handleOverlayOpen() {
		open = true;
	}
</script>

<main on:scroll={(ev) => console.log('ev : ', ev)}>
	<div class="flex flex-col items-center gap-4">
		<CallbackCard on:callback={handleOverlayOpen} />
		<Carousel />
		<!-- <button class="btn btn-primary w-40" on:click={handleOverlayOpen}> Open Overlay </button>
		<button class="btn btn-primary w-40" on:click={handleOverlayOpen}> Open Overlay </button> -->
		<Bottomsheet {open} on:close={() => (open = !open)}>
			<div class="p-6">
				<div class="flex flex-col gap-4 justify-center items-center">
					<h2 class="bold text-xl">Bottom Sheet Height</h2>
					<p class="text-gray-600 text-ellipsis">
						Lorem ipsum dolor, sit amet consectetur adipisicing elit. Est voluptate reiciendis
						perspiciatis, suscipit fugit expedita qui, doloribus quo iusto officia deserunt nam
						voluptates porro. Sed pariatur nemo sequi minima adipisci?
					</p>
					<button class="btn btn-primary w-40" on:click={() => (open = false)}> Close </button>
				</div>
			</div>
		</Bottomsheet>
	</div>
</main>

<style lang="postcss">
	:global(html) {
		background-color: theme(colors.gray.200);
	}
</style>
