<script>
   import { onMount } from 'svelte';

  let games64bit = [];

  // Retrieve the "64bit" games and flatten them into a single array
  onMount(async () => {
    const response = await fetch('/data/games.json');
    const gameData = await response.json();
    games64bit = Object.values(gameData["64bit"].genre)
      .flatMap(genre => genre.games);
  });

  let selectedGame = null;

  function selectRandomGame() {
    selectedGame = games64bit[Math.floor(Math.random() * games64bit.length)];
  }
</script>

<main>
<h1>64-bit Games</h1>

<button on:click={selectRandomGame}>Select Random Game</button>

{#if selectedGame}
  <div>
    <h2>Random Game</h2>
    <p>Title: {selectedGame.title}</p>
    <p>Platform: {selectedGame.platform}</p>
    <p>Publisher: {selectedGame.publisher}</p>
    <p>Year: {selectedGame.year}</p>
  </div>
{/if}
</main>

<style>

</style>