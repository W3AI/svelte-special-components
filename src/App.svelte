<script>
  import Product from "./Product.svelte";
  import CartItem from "./CartItem.svelte";
  import FamilyNode from "./FamilyNode.svelte";

  let y;

  $: console.log(y);

  let currentTitle = 'My App';

  // Recursive Components
  let familyStructure = [
    {
      isParent: true,
      name: "Chris",
      children: [
        {
          isParent: true,
          name: "Moe",
          children: [{ isParent: false, name: "Julie" }]
        }
      ]
    },
    { isParent: false, name: "Anna" }
  ];

  // Dynamic Components code example
  let renderedComponent = { cmp: Product, title: "Test Product", id: "p1" };

  function toggle() {
    if (renderedComponent.cmp === Product) {
      renderedComponent = { cmp: CartItem, title: "Another Product", id: "p2" };
    } else {
      renderedComponent = { cmp: Product, title: "Test Product", id: "p1" };
    }
  }

  function switchTitle() {
      currentTitle = 'A New Title';
  }
</script>

<style>
  div {
    height: 1000px;
  }
</style>

<h3>Svelte: Accessing Window, Body and Head</h3>

<svelte:window bind:scrollY={y} />
<svelte:body on:mouseenter/>

<svelte:head>
    <title>{currentTitle}</title>
</svelte:head>

<button on:click={switchTitle} >Switch Title</button>

<hr>

<div>
  <!-- Dynamic Component Markup example -->
  <h3>Dynamic Component Example - To use for complex If/Else statements</h3>
  <button on:click={toggle}>Toggle Display</button>

  <svelte:component
    this={renderedComponent.cmp}
    title={renderedComponent.title}
    id={renderedComponent.id} />
  <hr />
  <!-- Recursive Components Markup -->
  <h3>Recursive Component Example</h3>
  {#each familyStructure as familyMember}
    <FamilyNode member={familyMember} />
  {/each}
</div>
