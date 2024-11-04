<script>
	// Exercise 1
	let count = 0;
	$: doubled = count * 2;

	$: if (count >= 5) {
		alert('count is too high!');
		count = 0;
	}

	function increment() {
		count += 1;
	}

	// Exercise 2
	let numbers = [1, 2, 3, 4];

	function addNumber() {
		numbers.push(numbers.length + 1);
		numbers = numbers;
	}

	$: sum = numbers.reduce((total, num) => total + num, 0);

	// Exercise 3
	import Nested from '../components/Nested.svelte';

	// Exercise 4
	import Info from '../components/Info.svelte';

	let data = {
		name: 'Carlos',
		age: 44,
		city: 'Berlin'
	};
</script>

<h1 class="rounded-md text-center text-3xl">Welcome to SvelteKit</h1>

<div class="mb-8">
	<h2>Exercise 1</h2>
	<p>{count} doubles is {doubled}</p>
	<button on:click={increment} class="rounded-md bg-green-500 px-2">
		Clicked {count}
		{count === 1 ? 'time' : 'times'}
	</button>
</div>

<div class="mb-8">
	<h2>Exercise 2</h2>
	<p>{numbers.join(' + ')} = {sum}</p>
	<button on:click={addNumber} class="rounded-md bg-blue-500 px-2">Add a number</button>
</div>

<div class="mb-8">
	<h2>Exercise 3</h2>
	<Nested answer={'44'} />
	<Nested />
</div>

<div>
	<h2>Exercise 4</h2>
	<Info {...data} />
</div>
