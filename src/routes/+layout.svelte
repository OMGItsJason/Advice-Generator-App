<script lang="ts">
	import '../app.css';
	import * as Card from '@/components/ui/card';
	import MobileDiv from '@/assets/images/pattern-divider-mobile.svg';
	import DesktopDiv from '@/assets/images/pattern-divider-mobile.svg';
	import Dice from '@/assets/images/icon-dice.svg';
	import { Button } from '@/components/ui/button';
	let { children } = $props();

	let isAdviceGenerated: boolean = $state(false);
	let advice: string = $state('');
	let adviceId: number = $state(0);

	const generateAdvice = async () => {
		if (!isAdviceGenerated) {
			isAdviceGenerated = true;
		}
		const url = await fetch('https://api.adviceslip.com/advice'); // Fetching API
		const response = await url.json(); // Parsing JSON
		const { slip } = response; // Destructuring the response
		advice = slip.advice; // Extracting the advice
		adviceId = slip.id; // Extracting the advice id
	};
</script>

<div class="flex h-svh w-svw items-center justify-center bg-cyan-950 px-10 md:px-60">
	<Card.Root class="relative border-0 bg-white/40 text-center">
		<Card.Header>
			<Card.Title class="text-base font-bold uppercase tracking-wider text-green-500 md:text-xl">
				Advice #<span>{isAdviceGenerated ? adviceId : 0}</span>
			</Card.Title>
		</Card.Header>
		<Card.Content class="text-2xl font-semibold tracking-wide text-white">
			{#if !isAdviceGenerated}
				Generate Advice
			{:else}
				{#await generateAdvice()}
					Generating Advice...
				{:then slip}
					<blockquote>
						" {advice} "
					</blockquote>
				{/await}
			{/if}
		</Card.Content>
		<Card.Footer class="flex flex-col">
			<div class="w-full pb-8">
				<img src={MobileDiv} alt="pattern-divider" class="w-full md:hidden" />
				<img src={DesktopDiv} alt="pattern-divider" class="hidden w-full md:block" />
			</div>
			<Button
				size="icon"
				onclick={generateAdvice}
				class="absolute -bottom-8 size-14 rounded-full bg-green-500 hover:bg-green-400 hover:shadow-2xl hover:shadow-green-300"
			>
				<img src={Dice} alt="Dice" />
			</Button>
		</Card.Footer>
	</Card.Root>
</div>
{@render children()}
