<script>
  import { onDestroy } from 'svelte';

  export let colorPrincpal = 'bfea45';
  export let on = false;

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

<div style={`background-color: #${on ? colorPrincpal : color};`} />

<style>
  div {
    background-color: #49b293;
    width: 70px;
    height: 70px;
    margin: 1px;
    border-radius: 5px;
    /* border-bottom: 1px solid white; */
    -webkit-transition: background-color 500ms linear;
    -ms-transition: background-color 500ms linear;
    transition: background-color 500ms linear;
    /* transform: rotateX(60deg) rotateY(0deg) rotateZ(-45deg); */
  }
</style>
