<script>
  import gamesData from '../data/games.json';
  let games = Object.values(gamesData['64bit']['genre']).flatMap(genre => genre.games);
</script>

<main>
<h1>64-bit Games</h1>
<button on:click={() => games = []}>Clear List</button>
  <button on:click={() => games = Object.values(gamesData['64bit']['genre']).flatMap(genre => genre.games)}>All Games</button>
  <button on:click={() => games = gamesData['64bit']['genre'].racing.games}>Racing</button>
  <button on:click={() => games = gamesData['64bit']['genre'].sport.games}>Sport</button>

  <ul>
    {#each games as game}
      <li>{game.title} - {game.platform}</li>
    {/each}
  </ul>


</main>

<style>

</style>