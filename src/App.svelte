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
<div class="mx-auto px-4 bg-gray-100 font-rubik mb-7">
  <div class="mx-auto">
  <div class="flex items-center justify-center border border-transparent py-4 text-sm font-medium text-gray-700 hover:text-gray-500">
    <button
      on:click={prevPage}
      disabled={page === 1}
      class="w-20 focus:outline-none focus:ring-2 focus:ring-gray-500 focus:ring-offset-2 hover:bg-gray-700 shadow-sm leading-4 inline-flex text-gray-100 bg-gray-600 px-3 py-3 mr-3 rounded-md">
        Previous
    </button>
    <button
      on:click={nextPage}
      class="w-20 focus:outline-none focus:ring-2 focus:ring-gray-500 focus:ring-offset-2 leading-4 inline-flex justify-center text-gray-100 bg-gray-600 px-3 py-3 rounded-md">
      Next
    </button>
  </div>
    <div>
      <Character characters={characters}/>
    </div>
  </div>
</div>