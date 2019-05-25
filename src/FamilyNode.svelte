<script>
    export let member;
</script>

<h1>{member.name}</h1>
{#if member.isParent}
<ul>
    {#each member.children as child}
    <li>{child.name}</li>
    {/each}
</ul>
{/if}