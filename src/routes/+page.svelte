<script lang="ts">
	import { onMount } from "svelte";
	import CtaCard from "$components/CtaCard.svelte";
	import StakingCard from "$components/StakingCard.svelte";
	import AccordionFaq from "$components/AccordionFaq.svelte";
	import StatisticCardGrid from "$components/StatisticCardGrid.svelte";

	let visible = true,
		onLoad = false;

	onMount(() => {
		setTimeout(() => onLoad = true, 10)
	})
</script>

{#if onLoad}
	<div class="flex flex-col mt-20 mb-8">
		<div class="flex gap-14 lg:gap-24 justify-center lg:items-end w-full p-8 lg:flex-row flex-col">
			<CtaCard />
			<StakingCard />
		</div>
		<StatisticCardGrid />
		<AccordionFaq />
	</div>
{/if}