<script context="module">
  // Put here code that needs to run just once per module / file
  console.log("Runs once!");
</script>

<script>
  export let member;

  console.log("Runs multiple times!");
</script>

<style>
  div {
    margin-left: 2rem;
  }
</style>

<div>
  <h1>{member.name}</h1>
  {#if member.isParent}
    {#each member.children as child}
      <svelte:self member={child} />
    {/each}
  {/if}
</div>
