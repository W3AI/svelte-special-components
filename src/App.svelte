<script>
  import Product from "./Product.svelte";
  import CartItem from "./CartItem.svelte";



  // Dynamic Components code example
  let renderedComponent = { cmp: Product, title: "Test Product", id: "p1" };

  function toggle() {
    if (renderedComponent.cmp === Product) {
      renderedComponent = { cmp: CartItem, title: "Another Product", id: "p2" };
    } else {
      renderedComponent = { cmp: Product, title: "Test Product", id: "p1" };
    }
  }
</script>



<!-- Dynamic Component Markup example -->
<hr>
<h3>Dynamic Component Example - To use for complex If/Else statements</h3>
<button on:click={toggle}>Toggle Display</button>

<svelte:component
  this={renderedComponent.cmp}
  title={renderedComponent.title}
  id={renderedComponent.id} />
