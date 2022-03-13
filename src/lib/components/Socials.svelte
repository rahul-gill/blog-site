<script lang="ts">
    let siteUrl = ""

    let socials = [
        {
            name: "Github",
            href: "",
            icon: "fa fa-github"
        },
        {
            name: "Linkedin",
            href: "",
            icon: "fa fa-linkedin"
        },
        {
            name: "Stack Overflow",
            href: "",
            icon: "fa fa-stack-overflow"
        }
    ]
</script>

<div class="social">
    <!--TODO: search url-->
    <a href={siteUrl + ""} class="search-bar">
        <i class="fa fa-sm fa-search"></i>
    </a>
    <div class="social-links-bar">
        {#each socials as {name,href, icon}}
            <a {href} target="_blank" rel="noopener">
                <i class="social-icon {icon} fa-lg" aria-hidden="true"></i>
            </a>
        {/each}
    </div>
</div>

<style>
    .social{
        width: 100%;
        justify-content: center;
        display: flex;
        flex-direction: column;
    }
    .search-bar{
        text-align: center;
        width: 100%;
        margin-top: 1rem;
        margin-bottom: 0.5rem;
    }
    .social-links-bar{
        display: flex;
        justify-content: center;
        margin-bottom: 0.5rem;
    }
    .social-icon{
        color: var(--some-to-be-decided-color);
    }
</style>