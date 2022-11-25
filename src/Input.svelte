<script>
	import { getContext } from 'svelte'
	
	const pane = getContext('pane')
	
	export let params
	export let label = ''
	
	let nested = isNested()
	
	function isNested() {
		for (const key in params) {
			return typeof params[key] === 'object'
		}
	}
	
	function singleControl() {
		const paramObj = {
			[label]: params
		}
	
		pane.addInput(paramObj, label)
	
		pane.on('change', ({ presetKey, value }) => {
			params = value
		})
	}
	
	function nestedControls() {
		for (const param of Object.keys(params)) {
			pane.addInput(params, param)
			pane.on('change', ({ presetKey, value }) => {
				params[presetKey] = value
			})
		}
	}
	
	nested ? nestedControls() : singleControl()
</script>