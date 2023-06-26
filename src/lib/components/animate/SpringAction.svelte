<script>
	import spring from './spring.js';
	export let boopParams;
	let isBooped = false;
	
	// Is there a more Svelte-y way to do this?
	function setIsBooped(val) {
		isBooped = val;
	}
	
	function triggerBoop() {
		isBooped = true;
	}
</script>

<!-- trigger onclick so demo works on mobile -->
<span on:mouseenter={triggerBoop} on:mouseleave={() => isBooped = !isBooped} on:click={triggerBoop}  use:spring={{isBooped, ...boopParams, setter: setIsBooped}}>
	<slot/>
</span>