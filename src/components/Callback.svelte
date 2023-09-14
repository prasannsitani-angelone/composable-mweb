<script>
	import { goto } from '$app/navigation';
	import Card from './Card.svelte';
	import Bottomsheet from './Bottomsheet.svelte';

	let open = false;

	/**
	 * @type {any}
	 */
	export let item;

	const handleOpen = () => {
		open = true;
	};

	const handleClose = () => {
		open = false;
	};

	const handleSelfScreen = () => {
		goto('/detail');
	};
</script>

<main>
	<Card
		{item}
		on:self-overlay={handleOpen}
		on:self-screen={handleSelfScreen}
		on:external-overlay
		on:external-screen
	/>
	<Bottomsheet {open} on:close={handleClose} />
</main>
