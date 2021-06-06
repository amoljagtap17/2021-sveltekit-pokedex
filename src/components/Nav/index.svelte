<script>
	export let path
</script>

<nav class="flex justify-end w-full bg-gray-500 shadow-2xl">
	<a href="/" class={`mx-4 py-2 text-lg ${path === '/' && 'border-b-4 border-yellow-400'}`}>Home</a>
	<a
		href="/about"
		class={`mx-4 py-2 text-lg ${path === '/about' && 'border-b-4 border-yellow-400'}`}>About</a
	>
</nav>
