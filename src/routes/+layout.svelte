<script lang="ts">
	import '../app.postcss';
	import { MetaTags } from 'svelte-meta-tags';
	import NavigationBar from '$components/NavigationBar.svelte';
	import { Discord, GitHub, Twitter } from 'svelte-stacks-icons';
	//import { setInitialClassState } from "$components/ui/light-switch/light-switch";
	import Button from '$components/ui/button/Button.svelte';
</script>

<MetaTags 
	title="$FRANK - Frank Finance" 
	description="It ain't much, but it's honest work. Bringing fun back to DeFi."
	openGraph={{
    url: 'https://frankfinance.app/',
    title: 'Frank Finance',
    description: '$FRANK - It ain\'t much, but it\'s honest work.',
    images: [
      {
        url: 'https://i.imgur.com/ltZVSgA.png',
        width: 800,
        height: 600,
        alt: '$FRANK - It\'s honest work.'
      },
    ],
    site_name: 'FrankFinance'
  }}
	twitter={{
		handle: '@FrankTheFinance',
		site: '@FrankTheFinance',
		cardType: 'summary_large_image',
		description: '$FRANK - It ain\'t much, but it\'s honest work.',
		image: 'https://i.imgur.com/ltZVSgA.png',
		imageAlt: '$FRANK - Frank Finance.'
	}}
/>

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
