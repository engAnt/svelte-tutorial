<script>
	let m = { x: 0, y: 0 };

	function handleMousemove(event) {
		m.x = event.clientX;
		m.y = event.clientY;
	}


	let k = { x: 0, y: 0 };
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