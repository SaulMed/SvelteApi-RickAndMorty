<script>
    export let character;
</script>

<div  class="character">
    <img src={character.image} alt={character.name} />
    <h3>{character.name}</h3>
    <hr>
    <h5>{character.species}</h5>
</div>

