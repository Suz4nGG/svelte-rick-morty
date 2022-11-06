<script>
  export let characters;
  console.log(characters)
</script>
<ul class="grid grid-cols-1 gap-6 sm:grid-cols-2 md:grid-cols-3 lg:grid-cols-4">
  { #each characters as character }
  <div class="px-4 py-2 shadow rounded-lg col-span-1 bg-slate-50">
    <div class="divide-y divide-gray-200">
      <div class="flex justify-between py-2">
        <p>{character.name}</p>
      </div>
      <p class="py-2">{character.species}</p>
    </div>
    <div class="flex align-middle justify-center flex-col items-center">
      <img
        class="mx-auto h-32 w-32 flex-shrink-0 rounded-full"
        src={character.image} alt={character.name}
      />
      {#if character.status === "Alive"}
        <dd class="mt-3">
          <span
            class="
              rounded-full
              bg-green-100
              px-2 py-1
              text-xs font-medium text-green-800">
            Alive
          </span>
        </dd>
      {:else if character.status === "Dead"}
        <dd class="mt-3">
          <span
            class="
              rounded-full
              bg-red-100
              px-2 py-1
              text-xs font-medium text-red-800">
            Dead
          </span>
        </dd>
      {:else if character.status === "unknown"}
        <dd class="mt-3">
          <span
            class="
              rounded-full
              bg-yellow-100
              px-2 py-1
              text-xs font-medium text-yellow-800">
            Unknown
          </span>
        </dd>
      {/if}
    </div>
    <div class="pt-3">
      <p>
        Gender: {character.gender}
      </p>
      <p>
        Origin:
        <span>
          {character.origin.name}
        </span>
      </p>
      <p>Location:
        <span>
          {character.location.name}
        </span>
      </p>
    </div>
  </div>
  { /each }
</ul>