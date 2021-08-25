<script>
  import { createEventDispatcher } from 'svelte';
  import { fade } from 'svelte/transition';
  import Face from './Face.svelte';

  let glow = false;
  let on = false;

  const dispatcher = createEventDispatcher();

  const handleHover = () => {
    glow = true;
    // console.log('enter');
  };

  const handleUnhover = () => {
    glow = false;
  };

  const handleClick = () => {
    on = true;
    dispatcher('click');
  };
</script>

<div class="cubo" on:mouseenter={handleHover} on:mouseleave={handleUnhover} on:click={handleClick}>
  {#if glow}
    <span transition:fade class="glow-container" />
  {/if}
  <span class="top">
    <Face
      top={50}
      skewX={30}
      skewY={0}
      rotation={-30}
      scaleY={0.87}
      {glow}
      {on}
      colorPrincpal="3b726c"
    />
  </span>
  <span class="left">
    <Face
      top={-8.5}
      left={-30}
      skewX={30}
      skewY={0}
      rotation={30}
      {glow}
      {on}
      colorPrincpal="bfea45"
    />
  </span>
  <span class="right">
    <Face
      top={-66}
      left={31}
      skewX={-30}
      skewY={0}
      rotation={-30}
      {glow}
      {on}
      colorPrincpal="fdf6b8"
    />
  </span>
</div>

<style>
  div.cubo {
    position: relative;
    /* margin-top: 100px; */
    align-self: center;
  }

  div.cubo:hover {
    cursor: pointer;
  }

  span.glow-container {
    margin-left: 60px;
    margin-top: 120px;
    z-index: 0;
    position: absolute;

    -webkit-box-shadow: 0px 0px 39px 50px rgba(191, 234, 69, 0.77);
    box-shadow: 0px 0px 39px 50px rgba(191, 234, 69, 0.77);
  }
</style>
