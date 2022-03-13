<script context="module" lang="ts">
	export const prerender = true;
</script>


<script>

	import Counter from '$lib/Counter.svelte';
	import theme from '$lib/assets/ts/config.ts';
	import { onMount } from 'svelte';
	import SvelteMarkdown from "svelte-markdown";
	import mermaid from "mermaid";

	let mounted = false;
	let themeValue;

	onMount(() => {
		mounted = true
		mermaid.initialize({ startOnLoad: true, theme:'forest'});
	});



	theme.subscribe(value => {
		console.log("theme:",value);
		if(mounted) {
			document.body.classList.replace(themeValue, value);
		}
		themeValue = value;
	});

	function handleThemeChange(){
		if(themeValue === "theme-light") {
			theme.set("theme-dark")
		}
		else {
			theme.set("theme-light")
		}
	}

	export let markdown = `
  # This is a header

This is a paragraph.
$$x^2=4$$

\`\`\`mermaid
  graph TD
        A[Client] --> B[Load Balancer]
        B --> C[Server01]
        B --> D[Server02]
\`\`\`

* This is a list
* With two items
  1. And a sublist
  2. That is ordered
    * With another
    * Sublist inside

| And this is | A table |
|-------------|---------|
| With two    | columns |`
	let generateMermaidDivs = () => {
		//TODO: optimization
		let index = markdown.indexOf("```mermaid")
		while (index !== -1){
			let laterString = markdown.substring(index + 10, markdown.length)
			let endingTripleD = laterString.indexOf("```")
			markdown =
					markdown.substring(0, index) +
					`<div class="mermaid">` +
					laterString.substring(0, endingTripleD) +
					"</div>" +
					laterString.substring(endingTripleD + 3, laterString.length)
			index = markdown.indexOf("```mermaid")
		}
	}
	generateMermaidDivs()



</script>

<svelte:head>
	<title>Home</title>
</svelte:head>

<section>
	<h1>
		<div class="welcome">
			<picture>
				<source srcset="svelte-welcome.webp" type="image/webp" />
				<img src="svelte-welcome.png" alt="Welcome" />
			</picture>
		</div>

		to your new<br />SvelteKit app
	</h1>

	<button on:click={handleThemeChange}>
		Change Theme
	</button>

	<h2>
		try editing <strong>src/routes/index.svelte</strong>
	</h2>

	<SvelteMarkdown source={markdown} />



	<Counter />
</section>

<style>
	section {
		display: flex;
		flex-direction: column;
		justify-content: center;
		align-items: center;
		flex: 1;
	}

	h1 {
		width: 100%;
	}

	.welcome {
		position: relative;
		width: 100%;
		height: 0;
		padding: 0 0 calc(100% * 495 / 2048) 0;
	}

	.welcome img {
		position: absolute;
		width: 100%;
		height: 100%;
		top: 0;
		display: block;
	}
</style>
