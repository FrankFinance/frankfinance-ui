<script lang="ts">
	import { onMount } from "svelte";
	import CtaCard from "$components/CtaCard.svelte";
	import StakingCard from "$components/StakingCard.svelte";
	import AccordionFaq from "$components/AccordionFaq.svelte";
	import StatisticCardGrid from "$components/StatisticCardGrid.svelte";
	import { tokenPrice } from "$lib/stores/token";
	import { FRANK_TOKEN_CONTRACT } from "$lib/config";

	let visible = true,
		onLoad = false;
	
	const getTokenPrice = async () => {
		const res = await fetch(`https://api.dexscreener.com/latest/dex/tokens/${FRANK_TOKEN_CONTRACT}`);
		const { pairs } = await res.json();

		const priceUsd = pairs[0].priceUsd;
		tokenPrice.set(priceUsd);
	}

	onMount(() => {
		getTokenPrice();
		setTimeout(() => onLoad = true, 10)
	})
</script>

{#if onLoad}
	<div class="flex flex-col mt-16	mb-16">
		<div class="flex gap-14 lg:gap-8 justify-center lg:items-end w-full p-8 lg:flex-row flex-col">
			<CtaCard />
			<StakingCard />
		</div>
		<StatisticCardGrid />
	</div>
{/if}