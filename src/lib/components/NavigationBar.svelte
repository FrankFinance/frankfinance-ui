<script lang="ts">
	import { cn } from "$lib/utils";
	import ConnectWallet from "./ConnectWallet.svelte";
	//import LightSwitch from "./ui/light-switch/LightSwitch.svelte";

	let className: string | undefined | null = undefined;
	export { className as class };
</script>

<div class="border-b fixed inset-x-0 top-0 z-10 bg-primary-foreground">
	<div class="flex h-16 items-center px-4">
		<nav class={cn("flex items-center space-x-4 lg:space-x-6", className)}>
			<a
				href="/examples/dashboard"
				class="text-lg font-medium text-primary transition-colors hover:text-muted-foreground inline-flex items-center gap-1"
			>
			frankfinance.app
			</a>
		</nav>

		<nav class={cn("flex items-center space-x-4 lg:space-x-6 ml-auto", className)}>
			<!--<LightSwitch />-->
			<ConnectWallet />
		</nav>
	</div>
</div>
