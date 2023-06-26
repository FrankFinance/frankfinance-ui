<script lang="ts">
	import '../app.postcss';
	import NavigationBar from '$components/NavigationBar.svelte';
	import { Discord, GitHub, Twitter } from 'svelte-stacks-icons';
	import { setInitialClassState } from "$components/ui/light-switch/light-switch";
</script>

<svelte:head>
	<!-- This causes the new eslint-plugin-svelte: https://github.com/sveltejs/eslint-plugin-svelte/issues/492 -->
	{@html `<\u{73}cript nonce="%sveltekit.nonce%">(${setInitialClassState.toString()})();</script>`}
</svelte:head>

<NavigationBar />

<slot />
<div class="border-t fixed inset-x-0 bottom-0 w-full">
	<div class="w-full flex justify-center bg-primary-foreground p-2 items-center gap-x-2">
		<p class="text-sm text-muted-foreground">&copy; frankfinance.app -- socials: </p>
		<Discord />
		<Twitter />
		<GitHub />
	</div>
</div>
