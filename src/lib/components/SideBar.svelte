<script lang="ts">
    import CategoryNavigation from "./CategoryNavigation.svelte";
    import Socials from "./Socials.svelte";
    import TopDirsNaviagtion from "./TopDirsNaviagtion.svelte";

    let siteUrl = "#"
    let navBarTitle = "Blogs"

    let navItemsList = [
        {
            text: "Contents",
            href: "#"
        },
        {
            text: "List item 2",
            href: "#"
        }
    ];
</script>

<div id="header">
    <div class="container">
        <!--Title and top navigation links-->
        <div class="title-container">
            <a id="a-title" href="{siteUrl}">
                <h1 id="no-before">{navBarTitle}</h1>
            </a>
            <TopDirsNaviagtion/>
        </div>

        <br>

        <!--Blog/Notes' Category Navigation-->
        <CategoryNavigation
            title="Blogs"
            selectedIndex={0}
            {navItemsList}/>

        <!--Bottom bar with search and social links-->
        <div id="bottom-bar">
            <Socials/>
        </div>
    </div>
</div>
