<script lang="ts">
	import arbitrumLogo from '$lib/assets/arbitrum-logo.svg'

	import Button from './ui/button/Button.svelte';
	import { onMount } from 'svelte';

	import { defaultEvmStores as evm, connected, web3, selectedAccount, chainId, chainData } from 'svelte-web3'
	import SpringAction from './animate/SpringAction.svelte';
	import WalletHoverCard from './WalletHoverCard.svelte';
	import { FRANK_TOKEN_CONTRACT } from '$lib/config';
	import FRANK_TOKEN from '$lib/contracts/Frank.json';
	import { userBalance } from '$lib/stores/user';
	import { truncateMiddle } from '$lib/utils';

  let pending = false;

  const connect = async () => {
		pending = true;

		try {
			await evm.setProvider();
			pending = false;

			if(!$selectedAccount) {
				disconnect();
			}
		} catch (e) {
			console.log(e);
			disconnect();
		}
  }

  const disconnect = async () => {
    await evm.disconnect()
    pending = false
  }

	onMount(() => {
		connect();
	})

	selectedAccount.subscribe(async ($selectedAccount) => {
  	if (!$selectedAccount) return

		const contract = new $web3.eth.Contract(FRANK_TOKEN.abi, FRANK_TOKEN_CONTRACT);
		const tokenBalance = await contract.methods.balanceOf($selectedAccount).call();

		userBalance.set($web3.utils.fromWei(tokenBalance, 'ether'))
	})

</script>

<WalletHoverCard disconnect={disconnect}>
	<SpringAction boopParams={{ scale: 1.05, timing: 100}}>
		{#if !$connected}
			<Button variant="outline" on:click={() => { connect(); }}>
				<div class="flex items-center gap-x-2">
					<img src={arbitrumLogo} width="24"/>
					Connect
				</div>
			</Button>
		{:else}
			<Button variant="outline" on:click={() => { disconnect(); }}>
				<div class="flex items-center gap-x-2">
					<img src={arbitrumLogo} width="24"/>
					{#if $selectedAccount}
						{truncateMiddle($selectedAccount, 12)}
					{/if}
				</div>
			</Button>
		{/if}
	</SpringAction>
</WalletHoverCard>