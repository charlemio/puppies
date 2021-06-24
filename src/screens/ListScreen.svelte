<script>
	import { fade } from 'svelte/transition';
</script>

<div in:fade="{{duration: 200}}" class="text-left mx-5">
	<h1>The uggliest puppy:</h1>

	<img src="../static/puppy01.jpeg" alt="uggly puppy" />

	<hr />

	<h1>The most bullied puppy:</h1>

	<img src="../static/puppy00.jpeg" alt="bullied puppy" />

	<hr />

	<h1>The most retarded:</h1>

	<img src="../static/puppy04.jpeg" alt="retarded puppy" />

	<hr />

	<h1>The cuuuuutiiiiest:</h1>

	<img src="../static/puppy03.jpeg" alt="cutest puppy" />

	<hr />

	<h1>The most expensive puppy:</h1>

	<img src="../static/puppy02.jpeg" alt="expensive puppy" />
</div>

<style>
	h1 {
		@apply text-xl;
	}

	hr {
		@apply border-t-2;
		@apply rounded-full;
		@apply border-black;
		@apply border-opacity-50;
		@apply mx-8;
		@apply my-4;
	}

	img {
		@apply mt-2;
		@apply mb-6;
	}
</style>
