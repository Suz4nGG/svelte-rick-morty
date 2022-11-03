<script>
  export let characters;
</script>
<div>
  { #each characters as character }
    <div>{character.name}</div>
    <img src={character.image} alt={character.name}/>
  { /each }
</div>