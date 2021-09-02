<script>
  import Emphasis from './Emphasis.svelte';

  export let on = false;
</script>

<h2 class:on>scrum <Emphasis>of</Emphasis><br /> scrums</h2>

<style>
  h2 {
    color: white;
    font-size: 2.9em;
    text-align: right;
    line-height: 2.6rem;
    /* margin-top: -100px; */
  }
  .on {
    color: #3b726c;
  }
</style>
