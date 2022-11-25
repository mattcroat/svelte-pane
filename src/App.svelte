<script>
	import Pane from './Pane.svelte'
	import Input from './Input.svelte'
	import Folder from './Folder.svelte'
	
	let number = 200
	let color = '#ff0000'
	let obj = { x: 0, y: 0, z: 0 }
	let string = 'hello, world'
	let point = { x: 0, y: 0 }
	
	let item = {
		position: { x: 0, y: 0, z: 0 },
		scale: 1
	}
</script>

<Pane title="Pane">
	<Folder title="Controls">
		<Input bind:params={number} label="number" />
		<Input bind:params={obj} label="object" />
		<Input bind:params={string} label="string" />
		<Input bind:params={color} label="color" />
		<Input bind:params={point} label="point" />
	</Folder>
	
	<Folder title="Item">
		<Input bind:params={item} />
	</Folder>
</Pane>

<div style="width: 200px; border-radius: 16px;" style:height={number}px {number}px style:background={color} />

<pre>
	{JSON.stringify(item, null, 2)}
</pre>