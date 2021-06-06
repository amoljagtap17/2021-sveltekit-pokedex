<script context="module">
	export async function load({ page }) {
		const url = 'https://pokeapi.co/api/v2/pokemon?limit=20'
		const res = await fetch(url)
		const data = await res.json()

		const loadedPokemon = data.results.map((item, index) => {
			return {
				name: item.name,
				id: index + 1,
				image: `https://raw.githubusercontent.com/PokeAPI/sprites/master/sprites/pokemon/${
					index + 1
				}.png`
			}
		})

		return {
			props: {
				pokemon: loadedPokemon
			}
		}
	}
</script>

<script>
	// import { pokemon } from '../stores/pokestore'
	import PokemanCard from '../components/PokemanCard/index.svelte'

	export let pokemon
	let searchTerm = ''
	let filteredPokemon = []

	$: {
		if (searchTerm) {
			filteredPokemon = pokemon.filter(pokeman =>
				pokeman.name.toLowerCase().includes(searchTerm.toLowerCase())
			)
		} else {
			filteredPokemon = [...pokemon]
		}
	}
</script>

<svelte:head>
	<title>Svelte Kit Pokedex | Home</title>
</svelte:head>

<h1 class="text-4xl text-center my-8 uppercase">Svelte Kit Pokedex</h1>

<input
	type="text"
	placeholder="Search Pokemon"
	class="w-full rounded-md text-lg p-4 border-2 focus:outline-none border-gray-200 focus:border-gray-400"
	bind:value={searchTerm}
/>

<div class="py-4 grid gap-4 lg:grid-cols-3 md:grid-cols-2 grid-cols-1">
	{#each filteredPokemon as pokeman}
		<PokemanCard {pokeman} />
	{/each}
</div>
