<script>
	import { createEventDispatcher } from 'svelte';
	const dispatch = createEventDispatcher();

	export let items;
	export let activeItem;
</script>

<div class="tabs sticky top-0 bg-white mx-0 z-10 p-4 pb-0 mb-10 border-b-4 rounded-b-3xl border-red-200">
	<ul class="flex justify-center p-0 list-none text-center">
		{#each items as item}
			<li
				on:click={() => dispatch('tabChange', item)}
				class="m-0 sm:mx-2 cursor-pointer select-none text-gray-700 sm:font-bold"
				class:active={item === activeItem}
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
		color: rgb(255, 0, 0);
		@apply bg-red-100;
		border: 1px solid transparent;
		border-radius: 12px 12px 0px 0px;
		padding: 5px;
		animation-name: phaseInRedBackground;
		animation-duration: 0.3s;
	}

	.nonactive {
		border: 1px solid transparent;
		border-radius: 12px 12px 0px 0px;
		padding: 5px;
		animation-name: phaseOutRedBackground;
		animation-duration: 0.8s;
	}

	@keyframes phaseInRedBackground {
		0% {
			background-color: white;
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
