<script>
	const whiteImageUrl = '../static/puppyLight.svg';
	const blackImageUrl = '../static/puppy.svg';
</script>

<header class="flex flex-col items-center mx-8 pt-2 z-20 text-center text-xl text-black">
	<!-- {#if activeItem === 'Find A Puppy'}
		<img src={whiteImageUrl} alt="Cute puppy" class="object-contain w-20" />
	{:else} -->
	<img src={blackImageUrl} alt="Cute puppy" class="object-contain w-20" />
	<!-- {/if} -->
	<h1 class="text-3xl font-extrabold">PUPPY LAND</h1>
	<hr class="w-64  rounded-xl border-t-8 border-black" />
	<!-- {activeItem} -->
</header>

<style>
	h1 {
		font-family: 'Montserrat', sans-serif;
		/* font-weight: bolder; */
	}
</style>
