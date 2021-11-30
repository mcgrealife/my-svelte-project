<script>
	import Info from "./Info.svelte";
	export let name = "moog";
	let count = 0;
	$: doubled = count * 2;

	function incrementCount() {
		count += 1;
	}
	let code_sample2 = `function addNumber() {
		numbers = [...numbers, numbers.length + 1];
	}`;

	let code_sample1 = `function addNumber() {
	numbers.push(numbers.length + 1);
	numbers = numbers;
	}`;

	const pkg = {
		name: "svelte",
		version: 3,
		speed: "blazing",
		website: "https://svelte.dev",
	};
</script>

<main>
	<Info
		name={pkg.name}
		version={pkg.version}
		speed={pkg.speed}
		website={pkg.website}
	/>
	<Info {...pkg} />

	<h1>Hello {name}!</h1>
	<p>you've clicked the button <strong>{count}</strong> times!</p>
	<p>
		if you were clicking it in another multiverse, you would have clicked it <strong
			>{doubled}</strong
		> times!
	</p>
	<p>
		wow, what a great use of the <a
			href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/label"
			>javascript "labeled statement"</a
		>
	</p>

	<button on:click={incrementCount}> don't click this button </button>

	<p>Not {name}? Change your name here:</p> <input bind:value={name}>

	<h3>Benefits of Svelte</h3>
	<ul>
		<li>Intuitive syntax</li>
		<ul>
			<li>
				The the feeling of writing regular HTML and CSS with superpower <code
					>{"{"}variables{"}"}</code
				>
			</li>
			<li>
				the looping <code>#each</code>and control flow <code>#if</code>
			</li>
		</ul>
	</ul>

	<h3>Oddities of Svelte</h3>
	<ul>
		<li>
			<details>
				<summary
					>it doesn't work with functional methods like array.push.
					Instead, it requries re-assignment, like:</summary
				>
				<pre>
					<code>
						{code_sample1}
					</code>
					</pre>

				<p>or</p>

				<pre>
						<code>
							{code_sample2}
						</code>
						</pre>
			</details>
		</li>
		<li>
			It doesn't have a concept of "structs" or "interfaces" to define
			types or model data
		</li>
		<ul>
			<li>
				Maybe there is a different way, such as using typescript with
				svelte
			</li>
		</ul>
	</ul>

	<h3>Next Actions</h3>
	<ul>
		<li>test <a href="https://kit.svelte.dev/">Sveltekit</a></li>
		<li>test other methods of data flow, like stores</li>
		<li>test <a href="https://svelte.dev/blog/svelte-and-typescript">TypeScript</a> by adding <code>lang="ts"</code> into the <code>{'<'}script{'>'}</code> opening tag</li>
	</ul>
</main>

<style>
	main {
		text-align: center;
		padding: 1em;
		max-width: 240px;
		margin: 0 auto;
	}

	ul,
	h3 {
		text-align: left;
	}

	h1 {
		color: #ff3e00;
		text-transform: uppercase;
		font-size: 4em;
		font-weight: 100;
	}

	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}

	code {
		color: grey;
	}
</style>
