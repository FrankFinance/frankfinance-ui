<script>
	import { fade } from 'svelte/transition';
	import { DollarSign, Banknote, Users } from "lucide-svelte";
	import { Card, CardHeader, CardTitle, CardContent } from "$components/ui/card";
	import Skeleton from '$components/ui/skeleton/Skeleton.svelte';
	import { FRANK_TOKEN_CONTRACT } from '$lib/config';

	const tokenPrice = async () => {
		const res = await fetch(`https://api.dexscreener.com/latest/dex/tokens/${FRANK_TOKEN_CONTRACT}`);
		const { pairs } = await res.json();

		const priceUsd = pairs[0].priceUsd;
		return priceUsd;
	}
</script>

<div class="grid gap-4 md:grid-cols-2 lg:grid-cols-4 p-8 lg:mx-auto" in:fade|local={{ duration: 100 }}>
	<Card>
		<CardHeader
			class="flex flex-row items-center justify-between space-y-0 pb-2"
		>
			<CardTitle class="text-sm font-medium">
				Token Price
			</CardTitle>
			<DollarSign class="h-4 w-4 text-muted-foreground" />
		</CardHeader>
		<CardContent>
			<div class="text-2xl font-bold">
				{#await tokenPrice()}
					<Skeleton class="w-[100px] h-[20px]" />
				{:then priceUsd}
					{`$${priceUsd}`}
				{/await}
			</div>
		</CardContent>
	</Card>
	<Card>
		<CardHeader
			class="flex flex-row items-center justify-between space-y-0 pb-2"
		>
			<CardTitle class="text-sm font-medium">
				Market Cap
			</CardTitle>
			<Banknote class="h-4 w-4 text-muted-foreground" />
		</CardHeader>
		<CardContent>
			<div class="text-2xl font-bold">
				{#await tokenPrice()}
					<Skeleton class="w-[100px] h-[20px] rounded-full" />
				{:then priceUsd}
					{`$${(Number(priceUsd) * 7800000).toLocaleString()}`}
				{/await}
			</div>
		</CardContent>
	</Card>
	<Card>
		<CardHeader
			class="flex flex-row items-center justify-between space-y-0 pb-2"
		>
		<CardTitle class="text-sm font-medium">
			Total Supply
		</CardTitle>
		<Users class="h-4 w-4 text-muted-foreground" />
		</CardHeader>
		<CardContent>
			<div class="text-2xl font-bold">7,500,000</div>
			<p class="text-xs text-muted-foreground">
				17,500,000 has been burned.
			</p>
		</CardContent>
	</Card>
	<Card>
		<CardHeader
			class="flex flex-row items-center justify-between space-y-0 pb-2 md:space-x-44"
		>
			<CardTitle class="text-sm font-medium">
				Emissions
			</CardTitle>
			<Users class="h-4 w-4 text-muted-foreground" />
		</CardHeader>
		<CardContent>
			<div class="text-2xl font-bold">2,500</div>
			<p class="text-xs text-muted-foreground">
				$FRANK per day (boosted for 15d)
			</p>
		</CardContent>
	</Card>
</div>