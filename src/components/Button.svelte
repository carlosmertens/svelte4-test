<script>
	export let text;
	export let onClick;
	export let color = 'blue';
</script>

<button on:click={onClick} class={`rounded-md bg-${color}-400 px-2 hover:bg-${color}-30`}
	>{text}</button
>
