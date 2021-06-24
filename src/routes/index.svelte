<script>
	import { fade } from 'svelte/transition';

	import SwipeScreen from '../screens/SwipeScreen.svelte';
	import SellScreen from '../screens/SellScreen.svelte';
	import PuppyScreen from '../screens/ListScreen.svelte';
	import ShowPollsScreen from '../screens/ShowPollsScreen.svelte';
	import AddPollScreen from '../screens/AddPollScreen.svelte';
	import Tabs from '../shared/tabs.svelte';

	let items = ['Find A Puppy', 'Sell A Puppy', 'Puppy Lists', 'Add Poll'];
	export let activeItem = 'Find A Puppy';

	const tabChange = (e) => {
		activeItem = e.detail;
	};
</script>

<Tabs {items} bind:activeItem on:tabChange={tabChange} />
<div class="flex flex-col items-center min-h-screen max-w-md ">
	<br />
	{#if activeItem === 'Find A Puppy'}
		<SwipeScreen />
	{:else if activeItem === 'Sell A Puppy'}
		<SellScreen />
	{:else if activeItem === 'Puppy Lists'}
		<PuppyScreen />
	{:else if activeItem === 'Puppy Polls'}
		<ShowPollsScreen />
	{:else if activeItem === 'Add Poll'}
		<AddPollScreen />
	{:else}
		<p>Something has gone wrong...{activeItem}</p>
	{/if}
</div>
