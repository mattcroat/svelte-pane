<script>
	import { setContext } from 'svelte'
	import Tweakpane from 'https://cdn.jsdelivr.net/npm/tweakpane@3.1.0/dist/tweakpane.min.js'
	
	export let title
	
	const pane = new Tweakpane.Pane({ title })
	setContext('pane', pane)
</script>

<slot />