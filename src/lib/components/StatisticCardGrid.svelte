<script>
	import { fade } from 'svelte/transition';
	import { DollarSign, Banknote, Users } from "lucide-svelte";
	import { Card, CardHeader, CardTitle, CardContent } from "$components/ui/card";
</script>

<div class="grid gap-4 md:grid-cols-2 lg:grid-cols-4 p-8 lg:mx-auto" in:fade={{ duration: 100 }}>
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
			<div class="text-2xl font-bold">$0.00</div>
			<p class="text-xs text-green-600">
				+0.00% from yesterday
			</p>
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
			<div class="text-2xl font-bold">$100,000</div>
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
			<div class="text-2xl font-bold">15,000</div>
			<p class="text-xs text-muted-foreground">
				$FRANK per day - 30d left
			</p>
		</CardContent>
	</Card>
</div>