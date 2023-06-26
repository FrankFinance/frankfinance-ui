<script>
	import { Discord } from "svelte-stacks-icons";
	import { fade } from "svelte/transition";
	import SpringAction from "$components/animate/SpringAction.svelte";
	import { Button } from "$components/ui/button";
	import { Card, CardHeader, CardTitle, CardDescription, CardFooter } from "$components/ui/card";
	import arbitrumLogo from '$lib/assets/arbitrum-logo.svg';
	import sushiswapLogo from '$lib/assets/sushiswap-logo.svg';
	import farmerFrankLogo from '$lib/assets/frank-farmer.png'
</script>
<div class="flex flex-col gap-8 items-center" in:fade={{ duration: 100 }} >
	<Card class="w-full lg:max-w-xl">
		<CardHeader>
			<CardTitle>It ain't much, but it's honest work.</CardTitle>
			<CardDescription class="flex flex-col items-center gap-6">
				<p class="self-start">You'll need some $FRANK if you want to get your hands dirty, farmer. 
				Once you've done that, join us in our discord.</p>
				<img src={farmerFrankLogo} class="object-scale-down w-40 md:w-72" alt="Frank The Farmer" />
			</CardDescription>
		</CardHeader>
		<CardFooter class="flex justify-between">
			<SpringAction boopParams={{ scale: 1.05, timing: 100}}>
				<Button variant="outline" class="flex items-center gap-2">
					<img src={sushiswapLogo} class="w-6 h-6"/>
					Buy on Sushiswap
				</Button>
			</SpringAction>
			<span class="flex gap-2">
				<SpringAction boopParams={{ scale: 1.05, timing: 100}}>
					<Button variant="outline" class="w-10 rounded-full p-0" href="https://google.com" target="_blank">
						<Discord class="w-6 h-6" />
					</Button>
				</SpringAction>
				<SpringAction boopParams={{ scale: 1.05, timing: 100}}>
					<Button variant="outline" class="w-10 rounded-full p-0" href="https://arbiscan.io/token/0x408ed55cc16e71cd0f6770eef9bcd557d488a549" target="_blank">
						<img src={arbitrumLogo} class="w-6 h-6" />
					</Button>
				</SpringAction>
			</span>
		</CardFooter>
	</Card>
</div>