<script>
	let puppyIndex = 1;
	let puppyImgUrl = `../static/puppy0${puppyIndex}.jpeg`;

	const newPuppy = () => {
		puppyIndex = (puppyIndex + 1) % 6;
		puppyImgUrl = `../static/puppy0${puppyIndex}.jpeg`;
	};
</script>

<div class="flex flex-col items-center m-4">
	<div><img src={puppyImgUrl} alt="Cute puppies" class="object-contain h-96" /></div>
	<button
		class="w-40 rounded-xl bg-gray-500 hover:bg-gray-400 active:bg-gray-600 m-2 p-2 text-white focus:outline-none"
		on:click={newPuppy}><strong>New puppy?</strong></button
	>
</div>
