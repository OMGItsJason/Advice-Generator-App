<script lang="ts">
	import '../app.css';
	import * as Card from '@/components/ui/card';
	import MobileDiv from '@/assets/images/pattern-divider-mobile.svg';
	import DesktopDiv from '@/assets/images/pattern-divider-mobile.svg';
	import Dice from '@/assets/images/icon-dice.svg';
	import { Button } from '@/components/ui/button';
	let { children } = $props();
</script>

<div class="flex h-svh w-svw items-center justify-center bg-cyan-950 px-10 md:px-60">
	<Card.Root class="relative border-0 bg-white/40 text-center">
		<Card.Header>
			<Card.Title class="text-base font-bold uppercase tracking-widest text-green-500 md:text-xl"
				>Advice #</Card.Title
			>
		</Card.Header>
		<Card.Content class="text-2xl font-semibold tracking-wide text-white">
			" Lorem ipsum dolor sit amet consectetur adipisicing elit. Iusto nihil similique laboriosam
			harum magni saepe expedita voluptas natus iure magnam nostrum eligendi odio, esse quidem
			animi, autem sapiente ratione ab. "
		</Card.Content>
		<Card.Footer class="flex flex-col">
			<div class="w-full pb-8">
				<img src={MobileDiv} alt="pattern-divider" class="w-full md:hidden" />
				<img src={DesktopDiv} alt="pattern-divider" class="hidden w-full md:block" />
			</div>
			<Button
				size="icon"
				class="absolute -bottom-5 size-14 rounded-full bg-green-500 hover:bg-green-400 hover:shadow-2xl hover:shadow-green-300"
			>
				<img src={Dice} alt="Dice" />
			</Button>
		</Card.Footer>
	</Card.Root>
</div>
{@render children()}
