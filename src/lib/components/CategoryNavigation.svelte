<script lang="ts">
    export let title = "Blogs";
    export let navItemsList = [
        {
            text: "Contents",
            href: "#"
        }
    ];
    export let selectedIndex = 0;
</script>

<nav class="navbar navlinks">
    <button class="navbar-toggler"
            type="button"
            data-toggle="collapse"
            data-target="#navbarSupportedContent"
            aria-controls="navbarSupportedContent"
            aria-expanded="true"
            aria-label="Toggle navigation">
        <span>{title}</span>
        <i style="float: right;" class="fa fa-bars menu-icon" aria-hidden="true"></i>
    </button>

    <div class="navbar-collapse show" id="navbarSupportedContent">
        <div class="m-1 mt-2">
            <ul style="padding-top: 0.1em;">
                {#each navItemsList as {text, href}, i}
                    <li class="nav-item">
                        {#if i === selectedIndex}
                            <a {href} class="selected-nav-item">{text}</a>
                        {:else }
                            <a {href}>{text}</a>
                        {/if}
                    </li>
                {/each}
            </ul>

        </div>
    </div>
</nav>

<style>

    .navbar-toggler {
        /*TODO: collapsing*/
        width: 100%;
        display: flex;
        padding-left: 1em;
        padding-right: 1em;
        justify-content: space-between;
        font-size: 1em !important;
        outline: 0 solid transparent;
        border: none;
        background: none;
        color: var(--some-to-be-decided-color);
        text-align: left;
    }

    .nav-item{
        line-height: 1;
        padding-top: 0.4em;
    }
    .selected-nav-item{
        color:var(--selected-nav-item-color);
    }
</style>