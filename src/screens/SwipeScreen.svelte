<script>
	import { fade } from 'svelte/transition';
	import { Swipeable, Screen, } from 'buhrmi';

	let images = [
		{ url: '/puppy00.jpeg' },
		{ url: '/puppy01.jpeg' },
		{ url: '/puppy02.jpeg' },
		{ url: '/puppy03.jpeg' },
		{ url: '/puppy04.jpeg' },
		{ url: '/puppy05.jpeg' }
	];
</script>

<h1 class="z-20 fixed bottom-4 text-xl p-0 m-0 mx-auto text-center font-extrabold text-white">Would you buy this puppy?</h1>
<div id="black-bg" class="fixed bg-black z-0 w-full h-full top-0"></div>
<div id="top-gradient" class="fixed z-10 pointer-events-none top-0 w-full h-32 bg-gradient-to-b from-black to-transparent opacity-0"></div>
<div id="bot-gradient" class="fixed z-10 pointer-events-none bottom-0 w-full h-32 bg-gradient-to-t from-black to-transparent"></div>
<div in:fade={{ duration: 200 }} class="select-none">
	<div class="container">
		<Swipeable>
			<div class="images">
				{#each images as image}
					<Screen>
						<img class="img" src={image.url} alt="puppy">
					</Screen>
				{/each}
			</div>
		</Swipeable>
	</div>
</div>

<style>
	.container {
		padding-top: 150%;
		user-select: none;
		overflow: hidden;
		width: 100%;
	}
	.container :global(.swipeable) {
		position: fixed;
		top: 0;
		left: 0;
	}

	.img {
		object-fit: cover;
		background-size: cover;
		background-position: center;
		width: auto;
		height: 100%;
		margin: auto;
		z-index: -10;
	}
</style>
