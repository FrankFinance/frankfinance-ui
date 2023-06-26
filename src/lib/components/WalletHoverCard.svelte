<script lang="ts">
  import { connected, selectedAccount } from "svelte-web3";
  import { DollarSign } from "lucide-svelte";
  import { Avatar, AvatarFallback, AvatarImage } from "$components/ui/avatar";
  import {
    HoverCard,
    HoverCardContent,
    HoverCardTrigger
  } from "$components/ui/hover-card";
  import farmerFrank from '$lib/assets/frank-farmer.png';
	import { truncateMiddle } from "$lib/utils";
  import { userBalance } from "$lib/stores/user";
	import { Button } from "./ui/button";
  import { get } from "svelte/store";

  export let disconnect: () => void;

  let userBalanceString: number;
  
  $: {
    console.log($userBalance);
  }
</script>

<HoverCard>
  <HoverCardTrigger
    class="hover:underline underline-offset-4 rounded-sm focus-visible:outline-2 focus-visible:outline-offset-8 focus-visible:outline-black"
  >
    <slot />
  </HoverCardTrigger>
  {#if $connected && $selectedAccount}
    <HoverCardContent class="w-80 m-2 mt-4 mr-3 space-y-4">
      <div class="flex justify-between space-x-4">
        <Avatar>
          <AvatarImage src={farmerFrank} />
          <AvatarFallback>0x</AvatarFallback>
        </Avatar>
        <div class="space-y-1">
          <h4 class="text-sm font-semibold">{truncateMiddle($selectedAccount, 12)}</h4>
          <p class="text-sm">Avid farmer. Keep up the good work.</p>
          <div class="flex items-center pt-2">
            <DollarSign class="h-2 w-2 opacity-70" />{" "}
            <span class="text-xs text-muted-foreground">
              {#if $userBalance}
                {Number($userBalance).toLocaleString()} $FRANK
              {/if}
            </span>
          </div>
        </div>
      </div>
      <Button class="w-full" on:click={disconnect}>Disconnect</Button>
    </HoverCardContent>
  {/if}
</HoverCard>