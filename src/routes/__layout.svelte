<script>
	import '$lib/assets/scss/global.scss'
	import '$lib/assets/scss/responsive.scss'
	import SideBar from "$lib/components/SideBar.svelte";
	import Socials from "$lib/components/Socials.svelte";
	import {onMount} from "svelte";

	let topScroll, scrollFunction, topFunction;


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