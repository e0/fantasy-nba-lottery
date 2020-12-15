<script>
  import { onMount } from 'svelte';

  const NUMBER_OF_BALLS = 14;
  const COMBINATION_LENGTH = 4;

  let balls = [];
  let combination = [];
  $: result = combination.join('-');

  function resetBalls() {
    balls = Array.from({length:NUMBER_OF_BALLS},(_,k)=>k+1);
  }

  onMount(resetBalls);

  function getRandomIntBetween(min, max) {
    return Math.random() * (max - min) + min;
  }

  function generateCombination() {
    if (balls.length <= NUMBER_OF_BALLS - COMBINATION_LENGTH) {
      resetBalls();
      return;
    }

    if (balls.length === NUMBER_OF_BALLS) {
      combination = [];
    }

    const ballIndex = getRandomIntBetween(0, balls.length);
    const [ball] = balls.splice(ballIndex, 1);
    combination = [...combination, ball];
    generateCombination();
  }
</script>

<style>
</style>

<div>{result}</div>
<button on:click={generateCombination}
  class="py-2 px-4 bg-purple-500 text-white font-mono rounded-lg shadow-md hover:bg-purple-700 focus:outline-none">
  generate
</button>
