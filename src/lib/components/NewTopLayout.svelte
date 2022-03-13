<script>
    import SideBar from "./SideBar.svelte";
    import Socials from "./Socials.svelte";
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
            document.body.scrollTop = 0;
            document.documentElement.scrollTop = 0;
        }
        window.onscroll = function () { scrollFunction() };
    })


    // $(window).on('load', function () {
    //
    //     $('a[download]').each((i, e) => {
    //         $(e).addClass('fa fa-download');
    //     });
    // });

</script>


<SideBar/>


<div id="content" class="container">
    <section id="main_content">
        content
        <!--{% include anchor_headings.html anchorClass='anchor' h_max=2 html=content anchorBody="<i class='fa fa-link' aria-hidden='true'></i>" %}-->
    </section>
</div>


<button onclick="topFunction()" class="fa fa-arrow-up" id="top" title="Go to top"></button>

<footer>
    <Socials/>
</footer>