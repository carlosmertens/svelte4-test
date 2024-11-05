<script>
	export let text;
	export let onClick;
</script>

<button on:click={onClick} class="rounded-md bg-blue-400 px-2 hover:bg-blue-300">{text}</button>
