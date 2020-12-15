<script>
  import { onMount } from 'svelte';

  const NUMBER_OF_BALLS = 14;
  const COMBINATION_LENGTH = 4;

  let balls = [];
  let combination = [];


  function resetBalls() {
    balls = Array.from({length:NUMBER_OF_BALLS},(_,k)=>k+1);
  }

  function resetCombination() {
    combination = Array.from({length:COMBINATION_LENGTH}, () => '?');
  }

  onMount(() => {
    resetBalls();
    resetCombination();
  });

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

<div class="flex flex-col">
  <div class="bg-gray-900 m-x p-3 rounded">
    <div class="flex justify-around bg-gray-700 p-2 rounded-xl">
      {#each combination as num}
        <span class="text-gray-100 text-5xl">{num}</span>
      {/each}
    </div>
  </div>
  <button on:click={generateCombination}
    class="mt-3 py-2 px-4 bg-green-600 text-white font-mono rounded-lg shadow-md hover:bg-green-800 focus:outline-none">
    generate
  </button>
</div>
