<script>
	export let type = 'primary';
	export let flat = false;
	export let inverse = false;
</script>

<button class="{type} mx-2" class:flat={flat} class:inverse={inverse}><slot /></button>

<style>
	button {
		border: 0;
		cursor: pointer;
		user-select: none;
		border-radius: 8px;
		padding: 8px 16px;
		font-weight: bold;
		box-shadow: 2px 3px 5px rgba(0, 0, 0, 0.4);
    outline: 0px solid transparent;
	}

	.primary {
    background-color: #000;
    color: white;
	}

  .primary.inverse {
    background-color: #fff;
    color: black;
    border: 3px solid black;
  }

  .reject {
    background-color: #d34;
    color: white;
  }

  .reject.inverse {
    background-color: white;
    color: #d34;
    border: 3px solid #d34;
  }

  .accept {
    background-color: #3c6;
    color: white;
  }

  .accept.inverse {
    background-color: white;
    color: #3c6;
    border: 3px solid #3c6;
  }

  .flat {
    box-shadow: none;
  }
</style>
