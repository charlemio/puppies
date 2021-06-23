<script>
	import Button from '../shared/button.svelte';
	import Swipeable from '../shared/swipeable.svelte';
	import { tick } from 'svelte';

	let puppyIndex = 1;
	let puppyImgUrl = `../static/puppy0${puppyIndex}.jpeg`;

	let loginProgress, loginSwipeable, introProgress, zoomOut;
	tick().then(() => (zoomOut = true));

	// const newPuppy = () => {
	// 	puppyIndex = (puppyIndex + 1) % 6;
	// 	puppyImgUrl = `../static/puppy0${puppyIndex}.jpeg`;
	// 	console.log('New puppy');
	// };

</script>

<div class="select-none">
	<h1>Would you buy this puppy?</h1>
	<div>
		<Button type="reject" flat>Nah...</Button>
		<Button type="accept" flat>Yes!</Button>
	</div>
</div>

<style>
</style>
