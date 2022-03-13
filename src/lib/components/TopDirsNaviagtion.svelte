<script lang="ts">
    let topDirs = [
        {
            dirName: "Notes",
            href:  "#"
        },
        {
            dirName: "Blogs",
            href:  "#"
        }
    ];
</script>

<small class="nav-main">
    {#each topDirs as {dirName, href}, i}
        <a {href}>{dirName}</a>
        {#if i !== topDirs.length -1 }
            &nbsp;<span class="dir-separator">|</span>&nbsp;
        {/if}
    {/each}
</small>


<style>
    .dir-separator{
        color: #b5e853;
    }
</style>