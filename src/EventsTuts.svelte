<script>
	import Inner from './Inner.svelte';
	import Outer from './Outer.svelte';
	import CustomButton from './CustomButton.svelte';


	let m = { x: 0, y: 0 };

	function handleMousemove(event) {
		m.x = event.clientX;
		m.y = event.clientY;
	}


	let k = { x: 0, y: 0 };

	function handleClick() {
		alert("no more alerts");
	}


	function handleMessage(event) {
		alert(event.detail.text);
	}


	function handleClick2() {
		alert('custom button clicked');
	}

</script>


<style>
	div { width: 100%; height: 100px; }
</style>


<div on:mousemove={handleMousemove}>
	The mouse position is {m.x} x {m.y}
</div>

<div on:mousemove="{e => k = { x: e.clientX, y: e.clientY }}">
	The mouse position is {k.x} x {k.y}
</div>

<button on:click|once={handleClick}>Click me</button>
<br/><br/>

<Inner on:message={handleMessage}/>
<br/><br/>

<Outer on:message={handleMessage}/>
<br/><br/>

<CustomButton on:click={handleClick2}/>