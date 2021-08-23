<script>
  import Face from './Face.svelte';
</script>

<div class="cubo">
  <span class="top">
    <Face skewX={30} skewY={0} rotation={-30} scaleY={0.87} />
  </span>
  <span class="left">
    <Face top={30} left={-100} skewX={30} skewY={0} rotation={30} />
  </span>
  <span class="right">
    <Face top={-273} left={101} skewX={-30} skewY={0} rotation={-30} />
  </span>
</div>

<style>
  div.cubo {
    position: relative;
  }
</style>
