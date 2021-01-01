<script>
  import { onMount } from 'svelte';
  import Band from './Band.svelte';

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
  <div class="p-3 bg-gray-900 rounded m-x">
    <div class="flex justify-around p-2 bg-gray-700 rounded-xl">
      {#each combination as num}
        <span class="text-5xl text-gray-100">{num}</span>
      {/each}
    </div>
  </div>
  <button on:click={generateCombination}
    class="px-4 py-2 mt-3 font-mono text-gray-100 bg-green-600 rounded-lg shadow-md hover:bg-green-800 focus:outline-none">
    generate
  </button>
  <Band items={balls} />
</div>
