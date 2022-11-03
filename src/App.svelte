<script>
import Character from "./lib/Character.svelte"
let characters = []
let page = 1
async function getCharacters() {
  const response = await fetch(`https://rickandmortyapi.com/api/character?page=${page}`)
  const data = await response.json()
  characters = data.results
}
const nextPage = () => { page++; getCharacters() }
const prevPage = () => { page --; getCharacters() }
getCharacters()
</script>
<div>
  <button on:click={prevPage} disabled={page === 1}>Previous</button>
  <button on:click={nextPage}>Next</button>
</div>
<div>
  <Character characters={characters}/>
</div>