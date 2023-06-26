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

<div class="flex justify-center items-center w-full p-8 flex-col gap-4" in:fade={{ duration: 100 }}>
  <h1 class="font-medium text-lg">Frequently asked questions</h1>
  <div class="w-full max-w-7xl pt-2">
    <Separator class="max-w-6xl" />
    <Accordion type="single" collapsible class="w-full">
      <AccordionItem value="item-1">
        <AccordionTrigger>How does this work?</AccordionTrigger>
        <AccordionContent>
          Yes. It adheres to the WAI-ARIA design pattern.
        </AccordionContent>
      </AccordionItem>
      <AccordionItem value="item-2">
        <AccordionTrigger>Can I get in touch with the team?</AccordionTrigger>
        <AccordionContent>
          Yes. It comes with default styles that matches the other components'
          aesthetic.
        </AccordionContent>
      </AccordionItem>
      <AccordionItem value="item-3">
        <AccordionTrigger>Why are yields so high?</AccordionTrigger>
        <AccordionContent>
          Yes. It's animated by default, but you can disable it if you prefer.
        </AccordionContent>
      </AccordionItem>
    </Accordion>
  </div>
</div>