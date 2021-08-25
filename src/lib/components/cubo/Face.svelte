<script>
  import Pieza from './Pieza.svelte';

  export let skewX = 30;
  export let skewY = 0;
  export let scaleY = 0.87;
  export let rotation = -30;

  export let left = 0;
  export let right = 0;
  export let top = 0;

  export let glow = false;
  export let on = false;

  export let colorPrincpal = 'bfea45';
</script>

<div
  style={`margin-top: ${top}px; margin-left: ${left}px; margin-right: ${right}px; transform: rotate(${rotation}deg) skewX(${skewX}deg) skewY(${skewY}deg) scaleY(${scaleY})`}
>
  <div class="row">
    <Pieza {glow} {colorPrincpal} {on} />
    <Pieza {glow} {colorPrincpal} {on} />
    <Pieza {glow} {colorPrincpal} {on} />
  </div>
  <div class="row">
    <Pieza {glow} {colorPrincpal} {on} />
    <Pieza {glow} {colorPrincpal} {on} />
    <Pieza {glow} {colorPrincpal} {on} />
  </div>
  <div class="row">
    <Pieza {glow} {colorPrincpal} {on} />
    <Pieza {glow} {colorPrincpal} {on} />
    <Pieza {glow} {colorPrincpal} {on} />
  </div>
</div>

<style>
  div.row {
    display: flex;
    flex-direction: row;
    flex-wrap: nowrap;
    margin-left: 30px;
  }
</style>
