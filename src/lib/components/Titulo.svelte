<script>
  import Emphasis from './Emphasis.svelte';

  export let on = false;
</script>

<h2 class:on>scrum <br />of<Emphasis>scrum</Emphasis></h2>

<style>
  h2 {
    color: #6eceb2;
    font-size: 2.9em;
    text-align: left;
    line-height: 2.6rem;
    /* margin-top: -100px; */
  }
  .on {
    color: #6eceb2;
  }
</style>
