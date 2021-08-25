<script>
  import { onDestroy } from 'svelte';

  export let colorPrincpal = 'bfea45';
  export let on = false;
  export let glow = false;

  const colores = ['bfea45', 'def4a5', 'dee5e9', 'b6dcf9', '3b726c', 'fdf6b8', 'aaacef', 'b4c6f2'];

  const obtenerColor = () => {
    return colores[Math.floor(Math.random() * colores.length)];
  };

  let color = obtenerColor();
  let interval;
  const timeout = setTimeout(() => {
    color = obtenerColor();
    interval = setInterval(() => {
      let color2 = obtenerColor();
      while (color2 === color) color2 = obtenerColor();

      color = color2;
    }, 700 + Math.random() * 100);
  }, Math.random() * 100);

  onDestroy(() => {
    clearTimeout(timeout);
    clearInterval(interval);
  });
</script>

<div class:glow style={`background-color: #${on ? colorPrincpal : color};`} />

<style>
  div {
    background-color: #49b293;
    width: 20px;
    height: 20px;
    border: 1px solid #13213d;
    border-radius: 2.5px;
    border-color: #13213d;
    /* border-bottom: 1px solid white; */
    -webkit-transition: background-color 500ms linear;
    -ms-transition: background-color 500ms linear;
    transition: background-color 500ms linear;
    /* transform: rotateX(60deg) rotateY(0deg) rotateZ(-45deg); */
  }
</style>
