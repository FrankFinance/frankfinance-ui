<script lang="ts">
  import { fade } from "svelte/transition";
  import { Button } from "$components/ui/button";
  import {
    Card,
    CardContent,
    CardDescription,
    CardFooter,
    CardHeader,
    CardTitle
  } from "$components/ui/card";
  import {
    Tabs,
    TabsContent,
    TabsList,
    TabsTrigger
  } from "$components/ui/tabs";
  import {
    Tooltip,
    TooltipContent,
    TooltipProvider,
    TooltipTrigger
  } from "$components/ui/tooltip";
  import { DollarSign, HashIcon, PercentIcon } from "lucide-svelte";
</script>

<div in:fade|local={{ duration: 100 }} > 
  <Tabs value="stake" class="lg:max-w-2xl">
    <TabsList class="grid w-full grid-cols-2">
      <TabsTrigger value="stake">Stake</TabsTrigger>
      <TabsTrigger value="claim">Claim</TabsTrigger>
    </TabsList>
    <TabsContent value="stake">
      <Card>
        <CardHeader class="space-y-1">
          <CardTitle>Stake your $FRANK</CardTitle>
          <CardDescription>
            Stake your $FRANK to start receiving a subsidized yield - first 30 days have boosted emissions. Staking begins June 29th.
          </CardDescription>
        </CardHeader>
        <CardContent class="grid gap-6">
          <div class="relative">
            <div class="absolute z-0 inset-0 flex items-center">
              <span class="w-full border-t" />
            </div>
            <div class="relative flex justify-center text-xs uppercase">
              <span class="bg-background px-2 text-muted-foreground">
                Statistics
              </span>
            </div>
          </div>
          <Card>
            <CardHeader
              class="flex flex-row items-center justify-between space-y-0 pb-2"
            >
              <CardTitle class="text-sm font-medium">
                Total Value Locked (TVL)
              </CardTitle>
              <DollarSign class="h-4 w-4 text-muted-foreground" />
            </CardHeader>
            <CardContent>
              <div class="text-2xl font-bold">$0.00</div>
              <p class="text-xs text-green-600">
                +0.00% in 24 hours
              </p>
            </CardContent>
          </Card>
          <Card>
            <CardHeader
              class="flex flex-row items-center justify-between space-y-0 pb-2"
            >
              <CardTitle class="text-sm font-medium">
                APR
              </CardTitle>
              <PercentIcon class="h-4 w-4 text-muted-foreground" />
            </CardHeader>
            <CardContent>
              <div class="text-2xl font-bold">1,200%</div>
            </CardContent>
          </Card>
        </CardContent>
        <CardFooter>
          <TooltipProvider>
            <Tooltip>
              <TooltipTrigger class="w-full">
                <Button variant="outline" class="w-full" disabled>
                  Stake
                </Button>
              </TooltipTrigger>
              <TooltipContent class="bg-red-100 w-full">
                <p>Unavailable until 06/29</p>
              </TooltipContent>
            </Tooltip>
          </TooltipProvider>
          
        </CardFooter>
      </Card>
    </TabsContent>
    <TabsContent value="claim">
      <Card>
        <CardHeader class="space-y-1">
          <CardTitle>Your Position</CardTitle>
          <CardDescription>
            Claim your farming rewards or withdraw your staked funds. Remember, the longer you stake the more you earn!
          </CardDescription>
        </CardHeader>
        <CardContent class="grid gap-6">
          <div class="relative">
            <div class="absolute inset-0 flex items-center">
              <span class="w-full border-t" />
            </div>
            <div class="relative flex justify-center text-xs uppercase">
              <span class="bg-background px-2 text-muted-foreground">
                Statistics
              </span>
            </div>
          </div>
          <Card>
            <CardHeader
              class="flex flex-row items-center justify-between space-y-0 pb-2"
            >
              <CardTitle class="text-sm font-medium">
                Staked
              </CardTitle>
              <DollarSign class="h-4 w-4 text-muted-foreground" />
            </CardHeader>
            <CardContent>
              <div class="text-2xl font-bold">$0.00</div>
            </CardContent>
          </Card>
          <Card>
            <CardHeader
              class="flex flex-row items-center justify-between space-y-0 pb-2"
            >
              <CardTitle class="text-sm font-medium">
                Rewards
              </CardTitle>
              <DollarSign class="h-4 w-4 text-muted-foreground" />
            </CardHeader>
            <CardContent>
              <div class="text-2xl font-bold">$0.00</div>
              <p class="text-xs text-muted-foreground">
                0 $FRANK
              </p>
            </CardContent>
          </Card>
        </CardContent>
        <CardFooter>
          <TooltipProvider>
            <Tooltip>
              <TooltipTrigger class="w-full">
                <Button variant="outline" class="w-full" disabled>
                  Claim
                </Button>
              </TooltipTrigger>
              <TooltipContent class="bg-red-100 w-full">
                <p>Unavailable until 06/29</p>
              </TooltipContent>
            </Tooltip>
          </TooltipProvider>
        </CardFooter>
      </Card>
    </TabsContent>
  </Tabs>
</div>