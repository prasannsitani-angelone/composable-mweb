<script>
	import { goto } from '$app/navigation';

	function handleClick() {
		goto('/random');
	}
</script>

<main>
	<div>
		<h3>About Page</h3>
		<button class="btn btn-primary" on:click={handleClick}> Click Me </button>
	</div>
</main>
