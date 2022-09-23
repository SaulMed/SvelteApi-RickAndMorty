<script>
  import Character from "./libs/Character.svelte";

  let page = 1;
  let characters = [];

  const loadCharacters = async () => {
    const res = await fetch(
      "https://rickandmortyapi.com/api/character?page=" + page
    );
    const data = await res.json();
    characters = data.results;
  };

  loadCharacters();

  const prevPage = () => {
    page--;
    loadCharacters();
  };

  const nextPage = () => {
    page++;
    loadCharacters();
  };
</script>

<h1 class="title">Rick & Morty API</h1>
<hr>
<div class="container">
  <div class="buttons">
    <button class="btn" on:click={prevPage} disabled={page === 1 ? true : false}>Previus</button>
    <button class="btn" on:click={nextPage} disabled={page === 42 ? true : false}>Next</button>
  </div>

  <div class="grid">
    {#each characters as character}
      <Character {character} />
    {/each}
  </div>
</div>


<footer>This website was created by Saul Medina</footer>