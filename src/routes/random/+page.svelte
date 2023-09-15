<script>
	import { goto } from '$app/navigation';

	function handleClick() {
		goto('/random-2', {
			replaceState: true
		});
	}
</script>

<main>
	<div>
		<h3>Random Page</h3>
		<button class="btn btn-primary" on:click={handleClick}> Click Me </button>
	</div>
</main>
