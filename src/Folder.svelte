<script>
	import { getContext, setContext } from 'svelte'

	export let title
	export let expanded = true
	
	const pane = getContext('pane')
	const folder = pane.addFolder({ title, expanded })
	setContext('pane', folder)
</script>

<slot />