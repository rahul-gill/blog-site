<script lang="ts">
    import { slide } from 'svelte/transition';
    import {onMount} from "svelte";




    export let title = "Blogs";
    export let navItemsList = [
        {
            text: "Contents",
            href: "#"
        }
    ];
    export let selectedIndex = 0;
    let expanded = true;
    let changeExpandedState = () =>{
        expanded = !expanded;
    }
</script>

<nav class="navbar navlinks">
    <button class="navbar-toggler"
            type="button"
            data-toggle="collapse"
            data-target="#navbarSupportedContent"
            aria-controls="navbarSupportedContent"
            aria-expanded="true"
            aria-label="Toggle navigation"
            on:click={changeExpandedState}>
        <span>{title}</span>
        <i style="float: right;" class="fa fa-bars menu-icon" aria-hidden="true"></i>
    </button>
    {#if expanded}
    <div class="navbar-collapse show " id="navbarSupportedContent" transition:slide|local>
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
    {/if}
</nav>

<style>
    .navbar-collapse {
        opacity: 1;
        transition: opacity linear 1s, width linear 1s;
    }

    .navbar-collapse.collapsed {
        width: 0;
        opacity: 0;
    }

    .navbar-collapse .sub-section {
        padding: 10px;
        border-width: 2px;
        transition: padding linear 1s, border-width linear 1s;
    }

    .navbar-collapse .sub-section {
        padding: 10px 0;
        border-width: 2px 0;
    }

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