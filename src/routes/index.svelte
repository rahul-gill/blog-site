<script context="module" lang="ts">
	export const prerender = true;
</script>

<script lang="ts">
	import Counter from '$lib/Counter.svelte';
	import theme from '$lib/assets/ts/config.ts'


	let themeValue: string;

	theme.subscribe(value => {
		console.log("theme:",value);
		try {
			document.body.classList.replace(themeValue, value);
		}
		catch (e) {
			console.log("Error : ",e)
		}
		themeValue = value;
	});

	function handleThemeChange(){
		if(themeValue == "theme-light") theme.set("theme-dark")
		else theme.set("theme-light")
	}
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
