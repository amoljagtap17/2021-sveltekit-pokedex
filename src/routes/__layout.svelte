<script>
	import Nav from '../components/Nav/index.svelte'
</script>

<Nav />
<div class="container mx-auto my-4">
	<slot />
</div>

<style>
	@tailwind base;
	@tailwind components;
	@tailwind utilities;
</style>
