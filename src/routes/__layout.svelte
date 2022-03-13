<script>
	import '$lib/assets/scss/global.scss'
	import '$lib/assets/scss/responsive.scss'
	import SideBar from "$lib/components/SideBar.svelte";
	import Socials from "$lib/components/Socials.svelte";
	import {onMount} from "svelte";
	import renderMathInElement from "katex/contrib/auto-render";
	import mermaid from "mermaid";
	// import theme from "$lib/assets/ts/config.js";

	let topScroll, scrollFunction, topFunction, initializeMermaid, mounted = false;


	onMount(() => {
		topScroll = document.getElementById("top");
		scrollFunction = () => {
			if (document.body.scrollTop > 20 || document.documentElement.scrollTop > 20) {
				topScroll.style.display = "block";
			} else {
				topScroll.style.display = "none";
			}
		};
		topFunction = () => {
			window.scrollTo({top: 0, behavior: 'smooth'});
		}
		window.onscroll = function () { scrollFunction() };
		renderMathInElement(document.body, {
			// customised options
			// • auto-render specific keys, e.g.:
			delimiters: [
				{left: '$$', right: '$$', display: true},
				{left: '$', right: '$', display: false},
				{left: '\\[', right: '\\]', display: true},
				{left: '\\(', right: '\\)', display: false}
			],
			throwOnError : true
		});
		initializeMermaid = () => {
			mermaid.initialize({ startOnLoad: true, theme:'forest'});
		}
		initializeMermaid()
		mounted = true
	})
</script>


<SideBar/>


<div id="content" class="container">
	<section id="main_content">
		<main>
			<slot />
		</main>
	</section>
</div>


<button on:click={topFunction} class="fa fa-arrow-up" id="top" title="Go to top"></button>

<footer>
	<Socials/>
</footer>