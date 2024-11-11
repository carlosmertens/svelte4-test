<script>
	import Button from '../components/Button.svelte';

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

	// Exercise 5
	let user = { loggedIn: false };
	let x = 7;

	function toggle() {
		user.loggedIn = !user.loggedIn;
	}

	// Exercise 6
	let cats = [
		{ id: 'J---aiyznGQ', name: 'Keyboard Cat' },
		{ id: 'z_AbfPXTKms', name: 'Maru' },
		{ id: 'OUtn3pvWmpg', name: 'Henri The Existential Cat' }
	];

	// Exercise 7
	import Thing from '../components/Thing.svelte';

	let things = [
		{ id: 1, name: 'apple' },
		{ id: 2, name: 'banana' },
		{ id: 3, name: 'carrot' },
		{ id: 4, name: 'doughnut' },
		{ id: 5, name: 'egg' }
	];

	function handleRemove() {
		things = things.slice(1);
	}

	// Exercise 8
	async function getRandomNumber() {
		const res = '';

		return res;
	}

	let promise = getRandomNumber();

	function handleRandomNumber() {
		//
	}

	// Exercise 9
	let m = { x: 0, y: 0 };
</script>

<h1 class="rounded-md text-center text-3xl">Welcome to SvelteKit</h1>

<div class="mb-8">
	<h2 class="text-lg font-bold">Exercise 1</h2>
	<p>{count} doubles is {doubled}</p>
	<Button text={`Clicked ${count} ${count === 1 ? 'time' : 'times'}`} onClick={increment} />
</div>

<div class="mb-8">
	<h2 class="text-lg font-bold">Exercise 2</h2>
	<p>{numbers.join(' + ')} = {sum}</p>
	<Button text="Add a number" onClick={addNumber} />
</div>

<div class="mb-8">
	<h2 class="text-lg font-bold">Exercise 3</h2>
	<Nested answer={'44'} />
	<Nested />
</div>

<div class="mb-8">
	<h2 class="text-lg font-bold">Exercise 4</h2>
	<Info {...data} />
</div>

<div class="mb-8">
	<h2 class="text-lg font-bold">Exercise 5</h2>

	{#if user.loggedIn}
		<Button text="Log out" onClick={toggle} />
	{/if}

	{#if !user.loggedIn}
		<Button text="Log in" onClick={toggle} />
	{/if}

	{#if x > 10}
		<p>{x} is greater than 10</p>
	{:else if 5 > x}
		<p>{x} is less than 5</p>
	{:else}
		<p>{x} is between 5 and 10</p>
	{/if}
</div>

<div class="mb-8">
	<h2 class="text-lg font-bold">Exercise 6</h2>
	<ul>
		{#each cats as cat}
			<li>
				<a
					target="_blank"
					href="https://www.youtube.com/watch?v={cat.id}"
					rel="noreferrer"
					class="text-blue-950 underline">{cat.name}</a
				>
			</li>
		{/each}
	</ul>
</div>

<div class="mb-8">
	<h2 class="text-lg font-bold">Exercise 7</h2>

	<Button onClick={handleRemove} text="Remove first thing" />

	{#each things as thing (thing.id)}
		<Thing name={thing.name} />
	{/each}
</div>

<div class="mb-8">
	<h2 class="text-lg font-bold">Exercise 8</h2>
	<Button text="Get random number" onClick={handleRandomNumber} />

	{#await promise}
		<p>...waiting</p>
	{:then number}
		<p>The number is: {number}</p>
	{:catch error}
		<p style="color: red">{error.message}</p>
	{/await}
</div>

<div
	class="mb-8"
	on:mousemove={(e) => {
		m.x = e.clientX;
		m.y = e.clientY;
	}}
	role="article"
>
	<h2 class="text-lg font-bold">Exercise 9</h2>
	<div class="h-96 w-96 bg-red-200">The mouse position is {m.x} x {m.y}</div>
</div>

<div class="mb-8">
	<h2>Exercise 10</h2>
	<button class="rounded-md border-2 p-2" on:click|once={() => alert('I work only once')}
		>Click me</button
	>
</div>
