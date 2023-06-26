<script lang="ts">
	import { blur, fade } from 'svelte/transition';
  import {
    Accordion,
    AccordionContent,
    AccordionItem,
    AccordionTrigger
  } from "$components/ui/accordion";
	import { Separator } from "$components/ui/separator";
</script>

<div class="flex justify-center items-center w-full p-8 flex-col gap-4" in:fade|local={{ duration: 100 }}>
  <h1 class="font-medium text-lg">Frequently asked questions</h1>
  <div class="w-full max-w-7xl pt-2">
    <Separator class="max-w-6xl" />
    <Accordion type="single" collapsible class="w-full">
      <AccordionItem value="item-1">
        <AccordionTrigger>How does this work?</AccordionTrigger>
        <AccordionContent>
          We will be providing 10% of the total supply (after 75% has been burned) to incentivize staking rewards. Users can stake their FRANK/USDC LP to start earning rewards.
        </AccordionContent>
      </AccordionItem>
      <AccordionItem value="item-2">
        <AccordionTrigger>Can I get in touch with the team?</AccordionTrigger>
        <AccordionContent>
          Yes. You can reach out in our discord.
        </AccordionContent>
      </AccordionItem>
      <AccordionItem value="item-3">
        <AccordionTrigger>When will staking be available?</AccordionTrigger>
        <AccordionContent>
          Staking will be available on June 29th, 2023. Stay tuned for updates!
        </AccordionContent>
      </AccordionItem>
    </Accordion>
  </div>
</div>