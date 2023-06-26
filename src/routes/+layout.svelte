<script lang="ts">
	import '../app.postcss';
	import NavigationBar from '$components/NavigationBar.svelte';
	import { Discord, GitHub, Twitter } from 'svelte-stacks-icons';
	import { setInitialClassState } from "$components/ui/light-switch/light-switch";
	import Button from '$components/ui/button/Button.svelte';
</script>

<svelte:head>
	<!-- This causes the new eslint-plugin-svelte: https://github.com/sveltejs/eslint-plugin-svelte/issues/492 -->
	{@html `<\u{73}cript nonce="%sveltekit.nonce%">(${setInitialClassState.toString()})();</script>`}
</svelte:head>

<NavigationBar />

<slot />
<div class="border-t fixed inset-x-0 bottom-0 w-full">
	<div class="w-full flex justify-center bg-primary-foreground p-2 items-center">
		<p class="text-sm text-muted-foreground pr-4">&copy; frankfinance.app -- socials: </p>
		<Button variant="ghost" href="https://discord.gg/p3cKYHCS" target="_blank" class="w-12 rounded-md">
			<Discord  />
		</Button>
		<Button variant="ghost" href="https://twitter.com/FrankTheFinance" target="_blank" class="w-12 rounded-md">
			<Twitter />
		</Button>
		<Button variant="ghost" href="https://github.com/FrankFinance" target="_blank" class="w-12 rounded-md">
			<GitHub />
		</Button>
	</div>
</div>
