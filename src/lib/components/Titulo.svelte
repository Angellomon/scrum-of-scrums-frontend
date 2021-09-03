<script>
  import Emphasis from './Emphasis.svelte';

  export let on = false;
</script>

<h2 class:on>scrum of <br /><Emphasis>scrums</Emphasis></h2>

<style>
  h2 {
    color: white;
    font-size: 2.9em;
    text-align: left;
    line-height: 2.6rem;
    text-align: right;
    /* margin-top: -100px; */
  }
  .on {
    color: #6eceb2;
  }
</style>
