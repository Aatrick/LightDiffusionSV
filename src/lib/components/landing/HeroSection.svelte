<script lang="ts">
	import { ArrowRightIcon } from 'lucide-svelte';
	import AnimatedGradientText from '$lib/components/magic/AnimatedGradientText/AnimatedGradientText.svelte';
	import Particles from '$lib/components/magic/Particles/Particles.svelte';
	import BorderBeam from '$lib/components/magic/borderbeam/BorderBeam.svelte';
	import Button from '$lib/components/ui/button/button.svelte';
	import ThemeSwitcher from '$lib/components/ui/theme-switcher/theme-switcher.svelte';
	import type { ObserverEventDetails } from 'svelte-inview';
	import { inview } from 'svelte-inview';
	import { mode } from 'mode-watcher';

	// Images
	import HeroDarkImg from '$lib/imgs/hero-dark.png';
	import HeroLightImg from '$lib/imgs/hero-light.png';
	let inView = false;
	const handleChange = ({ detail }: CustomEvent<ObserverEventDetails>) => {
		// console.log(detail);
		inView = detail.inView;
	};
</script>

<section id="hero" class="relative mx-auto mt-20 max-w-7xl px-6 text-center md:px-8 z-10">
		<AnimatedGradientText class="w-fit inline-flex items-center justify-center  animate-fade-in">
			<span>✨ Introducing LightDiffusion</span>
			{' '}
			<ArrowRightIcon
				class="ml-1 size-3 transition-transform duration-300 ease-in-out group-hover:translate-x-0.5"
			/>
		</AnimatedGradientText>
	<h1
		class="-translate-y-4 animate-fade-in text-balance bg-gradient-to-br from-black from-30% to-black/40 bg-clip-text py-6 text-5xl font-medium leading-none tracking-tighter text-transparent opacity-0 [--animation-delay:200ms] dark:from-white dark:to-white/40 sm:text-6xl md:text-7xl lg:text-8xl"
	>
		LightDiffusion is the fastest
		<br class="hidden md:block" />
		{' '}
		Stable Diffusion GUI.
	</h1>
	<p
		class="mb-12 -translate-y-4 animate-fade-in text-balance text-lg tracking-tight text-gray-400 opacity-0 [--animation-delay:400ms] md:text-xl"
	>
		Retro-engineered to be the simplest, least complex, and most user-friendly.
	</p>
	<Button
		class="-translate-y-4 animate-fade-in gap-1 rounded-lg text-white opacity-0 ease-in-out [--animation-delay:600ms] dark:text-black"
	>
		<span>Get Started </span>
		<ArrowRightIcon
			class="ml-1 size-4 transition-transform duration-300 ease-in-out group-hover:translate-x-1"
		/>
	</Button>
	<div
		use:inview={{
			unobserveOnEnter: true,
			rootMargin: '-100px'
		}}
		on:inview_change={handleChange}
		class="relative mt-32 animate-fade-up opacity-0 [--animation-delay:400ms] [perspective:2000px] after:absolute after:inset-0 after:z-50 after:[background:linear-gradient(to_top,hsl(var(--background))_30%,transparent)]"
	>
		<div
			class="rounded-xl border border-white/10 bg-white bg-opacity-[0.01] before:absolute before:bottom-1/2 before:left-0 before:top-0 before:size-full before:opacity-0 before:[background-image:linear-gradient(to_bottom,var(--color-one),var(--color-one),transparent_40%)] before:[filter:blur(180px)] {inView
				? 'before:animate-image-glow'
				: ''}"
		>
			<BorderBeam
				size={200}
				duration={12}
				delay={0}
				colorFrom="var(--color-one)"
				colorTo="var(--color-two)"
			/>

			<img
				src={HeroDarkImg}
				alt="HeroDarkImage"
				class="relative hidden size-full rounded-[inherit] border object-contain dark:block"
			/>
			<img
				src={HeroLightImg}
				alt="HeroLightImage"
				class="relative block size-full rounded-[inherit] border object-contain dark:hidden"
			/>
		</div>
	</div>
</section>
{#if $mode === 'dark'}
	<Particles className="absolute inset-0" refresh={true} color="#ffffff" />
{:else}
	<Particles className="absolute inset-0" refresh={true} color="#000000"/>
{/if}