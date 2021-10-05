<script>
  import { fade } from 'svelte/transition';
  import { push } from 'svelte-spa-router';
  import Titulo from '../lib/components/Titulo.svelte';
  import { onDestroy } from 'svelte';
  import Cubo from '../lib/components/cubo/Cubo.svelte';

  let on = false;
  let redirect = false;
  let timeout;
  let timeout2;

  const URL = 'https://collaboration.merck.com/sites/SoFMexico/SitePages/sos.aspx';

  $: if (on) {
    timeout = setTimeout(() => {
      redirect = true;
    }, 3000);
  } else {
    clearTimeout(timeout);
  }
  $: if (redirect) {
    clearTimeout(timeout);
    timeout2 = setTimeout(() => {
      window.location.href = URL;
      // push('/info');
    }, 400);
  }
  onDestroy(() => clearTimeout(timeout2));
</script>

<section class:on transition:fade>
  {#if !redirect}
    <span class="titulo">
      <Titulo {on} />
    </span>
    <span class="cubo-container">
      <Cubo
        on:click={() => {
          on = true;
        }}
      />
    </span>
    {#if on}
      <div class="mensaje" transition:fade={{ duration: 400, delay: 200 }}>
        <p>powered by subsidiary of the future</p>
      </div>
    {:else}
      <span class="helper" transition:fade={{ duration: 250, delay: 300 }}>dale clic</span>
    {/if}
  {/if}
</section>

<style>
  span.titulo,
  span.cubo-container,
  span.helper,
  div.mensaje {
    position: absolute;
  }

  p {
    color: #75c7ae;
    text-align: center;
    margin: 0;
  }

  span.titulo {
    top: 5%;
  }

  span.cubo-container {
    bottom: 45%;
  }

  span.helper {
    color: white;
    /* color: #75c7ae; */
    text-align: center;
    bottom: 25%;
  }

  div.mensaje {
    bottom: 25%;
  }

  section {
    display: flex;
    flex-direction: column;
    align-items: center;

    background-color: #13213d;
    min-width: 100vw;
    min-height: 100vh;
    justify-content: space-between;
    position: relative;
  }
  .on {
    background-color: white;
    -webkit-transition: background-color 500ms linear;
    -ms-transition: background-color 500ms linear;
    transition: background-color 500ms linear;
  }
</style>
