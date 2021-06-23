<script>
	import SwipeScreen from '../components/swipeScreen.svelte';
	import SellScreen from '../components/sellScreen.svelte';
	import PuppyLists from '../components/puppyLists.svelte';
	import PuppyPolls from '../components/puppyPolls.svelte';
	import Tabs from '../shared/tabs.svelte';

	let items = ['Find A Puppy', 'Sell A Puppy', 'Puppy Lists', 'Puppy Polls'];
	let activeItem = 'Find A Puppy';

	const tabChange = (e) => {
		activeItem = e.detail;
	};
</script>

<Tabs {items} {activeItem} on:tabChange={tabChange} />
<div class="flex flex-col items-center min-h-screen max-w-md ">
	<br>
	{#if activeItem === 'Find A Puppy'}
		<SwipeScreen />
	{:else if activeItem === 'Sell A Puppy'}
		<SellScreen />
	{:else if activeItem === 'Puppy Lists'}
		<PuppyLists />
	{:else if activeItem === 'Puppy Polls'}
		<PuppyPolls />
	{:else}
		<p>Something has gone wrong...{activeItem}</p>
	{/if}
</div>
