<script>
	import { createEventDispatcher } from 'svelte';
	const dispatch = createEventDispatcher();

	export let items;
	export let activeItem;
</script>

<div
	class:opaque={activeItem !== 'Find A Puppy'}
	class="tabs sticky top-0 mx-0 z-10 px-2 sm:p-4  sm:pb-0 mt-2 mb-2 border-b-2 rounded-b-2xl rounded-t-lg border-red-200 bg-white bg-opacity-25"
>
	<ul class="flex justify-center p-0 list-none text-center">
		{#each items as item}
			<li
				on:click={() => dispatch('tabChange', item)}
				class:active={item === activeItem}
				class="p-0 m-0 sm:mx-0.5 cursor-pointer select-none text-black sm:font-bold hover:text-red-400 hover:bg-red-50"
				class:nonactive={item !== activeItem}
			>
				{item}
			</li>
		{/each}
	</ul>
</div>

<style>
	@media (max-width: 440px) {
		.tabs {
			font-size: 0.8em !important;
		}
	}

	@media (max-width: 360px) {
		.tabs {
			font-size: 0.6em !important;
		}
	}

	/* style for the currently activated tab item */
	.active {
		@apply text-red-600;
		@apply bg-red-100;
		border: 1px solid transparent;
		border-radius: 12px 12px 0px 0px;
		padding: 5px;
		animation-name: phaseInRedBackground;
		animation-duration: 0.2s;
	}

	.nonactive {
		border: 1px solid transparent;
		border-radius: 12px 12px 0px 0px;
		padding: 5px;
		animation-name: phaseOutRedBackground;
		animation-duration: 0.2s;
	}

	.opaque {
		background-color: white;
		@apply text-gray-700;
	}

	@keyframes phaseInRedBackground {
		0% {
			background-color: rgba(254, 242, 242, 1);
			left: 0px;
			top: 0px;
		}
		100% {
			background-color: rgba(254, 226, 226, 1);
			left: 0px;
			top: 0px;
		}
	}

	@keyframes phaseOutRedBackground {
		0% {
			background-color: rgba(254, 226, 226, 1);
			left: 0px;
			top: 0px;
		}
		100% {
			background-color: white;
			left: 0px;
			top: 0px;
		}
	}
</style>
