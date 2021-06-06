<script context="module">
	export async function load({ page }) {
		return {
			props: {
				path: page.path
			}
		}
	}
</script>

<script>
	import Nav from '../components/Nav/index.svelte'

	export let path
</script>

<Nav {path} />
<div class="container mx-auto my-4">
	<slot />
</div>

<style>
	@tailwind base;
	@tailwind components;
	@tailwind utilities;
</style>
