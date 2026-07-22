<script lang="ts">
import { onMount } from 'svelte';
	import { Button } from '$lib/components/ui/button';

	let mobileMenuOpen = $state(false);
	let showBackToTop = $state(false);

	const menuLinks = [
		{
			label: 'Services',
			href: '#services',
			icon: 'services',
			bg: 'bg-slate-900/70 hover:bg-slate-800/80',
			iconColor: 'text-slate-300'
		},
		{
			label: 'Offices',
			href: '#offices',
			icon: 'offices',
			bg: 'bg-slate-950/55 hover:bg-slate-800/80',
			iconColor: 'text-slate-300'
		},
		{
			label: 'What Sets Us Apart',
			href: '#what-sets-apart',
			icon: 'star',
			bg: 'bg-slate-900/70 hover:bg-slate-800/80',
			iconColor: 'text-slate-300'
		},
		{
			label: 'Get Started',
			href: '#get-started',
			icon: 'rocket',
			bg: 'bg-slate-950/55 hover:bg-slate-800/80',
			iconColor: 'text-slate-300'
		},
		{
			label: 'Contact',
			href: '#contact',
			icon: 'contact',
			bg: 'bg-slate-900/70 hover:bg-slate-800/80',
			iconColor: 'text-slate-300'
		}
	];

	const cities = [
		'Atlanta',
		'Chicago',
		'Cincinnati',
		'Dallas',
		'Denver',
		'Honolulu',
		'Las Vegas',
		'Los Angeles',
		'Memphis',
		'Miami',
		'New Orleans',
		'New York',
		'Orlando',
		'Phoenix',
		'Portland',
		'San Francisco',
		'San Jose',
		'Seattle',
		'Washington, DC',
		'And more'
	];

	onMount(() => {
		const updateBackToTopVisibility = () => {
			const threshold = window.innerWidth < 640 ? 250 : 500;
			showBackToTop = window.scrollY > threshold;
		};

		updateBackToTopVisibility();
		window.addEventListener('scroll', updateBackToTopVisibility, { passive: true });

		return () => window.removeEventListener('scroll', updateBackToTopVisibility);
	});
</script>

<main id="top" class="min-h-screen bg-[radial-gradient(circle_at_20%_0%,#1b3d62_0%,#0f2744_38%,#081a30_100%)] text-slate-100">
	<aside class="fixed top-0 left-0 z-30 hidden h-screen w-72 flex-col bg-[#0b213b]/85 p-6 backdrop-blur lg:flex">
		<a href="#services" aria-label="Home" title="Home" class="mb-8 block">
			<span class="inline-flex h-16 w-16 items-center justify-center rounded-2xl bg-white/10 text-white">
				<svg
					xmlns="http://www.w3.org/2000/svg"
					viewBox="0 0 24 24"
					fill="none"
					stroke="currentColor"
					stroke-width="2"
					stroke-linecap="round"
					stroke-linejoin="round"
					class="h-8 w-8"
				>
					<path d="M3 10.5 12 3l9 7.5" />
					<path d="M5 9.5V21h14V9.5" />
					<path d="M9 21v-6h6v6" />
				</svg>
			</span>
		</a>
		<nav class="space-y-2 text-sm">
			{#each menuLinks as link, index}
				<a
					href={link.href}
					class={`block rounded-lg border-l-2 border-transparent px-3 py-2 font-medium text-slate-100 transition hover:border-slate-400 hover:text-white ${link.bg} ${index % 2 === 0 ? 'shadow-[inset_0_1px_0_rgba(255,255,255,0.05)]' : ''}`}
				>
					<span class="inline-flex items-center gap-2">
						<svg
							xmlns="http://www.w3.org/2000/svg"
							viewBox="0 0 24 24"
							fill="none"
							stroke="currentColor"
							stroke-width="2"
							stroke-linecap="round"
							stroke-linejoin="round"
							class={`h-4 w-4 ${link.iconColor}`}
						>
							{#if link.icon === 'services'}
								<rect x="3" y="4" width="18" height="14" rx="2" />
								<path d="M8 20h8" />
							{:else if link.icon === 'offices'}
								<path d="M12 21s7-4.5 7-11a7 7 0 1 0-14 0c0 6.5 7 11 7 11Z" />
								<circle cx="12" cy="10" r="2.5" />
							{:else if link.icon === 'star'}
								<path d="m12 3 2.8 5.7 6.2.9-4.5 4.4 1.1 6.2L12 17.2 6.4 20.2l1.1-6.2L3 9.6l6.2-.9Z" />
							{:else if link.icon === 'rocket'}
								<path d="M5 19c2-1 3-2 4-4" />
								<path d="M15 5c3-1 6 2 5 5-1 3-4 6-7 7l-5-5c1-3 4-6 7-7Z" />
								<circle cx="14" cy="10" r="1" />
							{:else}
								<path d="M4 6h16v12H4z" />
								<path d="m4 8 8 5 8-5" />
							{/if}
						</svg>
						{link.label}
					</span>
				</a>
			{/each}
		</nav>
		<div class="mt-auto space-y-3">
			<p class="text-xs text-slate-200">
				<strong>Tech Support:</strong>
				<a href="tel:+18882832001" class="underline decoration-slate-400 underline-offset-2"
					>1.888.283.2001</a
				>
			</p>
			<p class="text-xs text-slate-200"><strong>24/7 Support:</strong> Chat with Us</p>
			<p class="text-xs text-slate-200">
				<strong>Support Documents:</strong>
				<a
					href="https://www.lexiconusa.com/support/"
					target="_blank"
					rel="noreferrer"
					class="underline decoration-slate-400 underline-offset-2"
					>Click Here</a
				>
			</p>
			<p class="text-xs text-slate-200">
				<strong>Privacy Policy and Terms of Use:</strong>
				<a
					href="https://lexiconusa.com/Terms-and-Services.html"
					target="_blank"
					rel="noreferrer"
					class="underline decoration-slate-400 underline-offset-2"
					>Click Here</a
				>
			</p>
		</div>
	</aside>

	<header class="fixed top-0 right-0 left-0 z-40 bg-[#0b213b]/90 px-4 py-3 backdrop-blur lg:hidden">
		<div class="mx-auto flex max-w-6xl items-center justify-between">
			<a
				href="#services"
				aria-label="Home"
				title="Home"
				class="inline-flex h-12 w-12 items-center justify-center rounded-lg bg-white/10 text-white"
			>
				<svg
					xmlns="http://www.w3.org/2000/svg"
					viewBox="0 0 24 24"
					fill="none"
					stroke="currentColor"
					stroke-width="2"
					stroke-linecap="round"
					stroke-linejoin="round"
					class="h-6 w-6"
				>
					<path d="M3 10.5 12 3l9 7.5" />
					<path d="M5 9.5V21h14V9.5" />
					<path d="M9 21v-6h6v6" />
				</svg>
			</a>
			<button
				type="button"
				onclick={() => (mobileMenuOpen = true)}
				class="inline-flex h-10 w-10 items-center justify-center rounded-md bg-white/10 text-white"
				aria-label="Open menu"
			>
				<span class="space-y-1">
					<span class="block h-0.5 w-5 bg-current"></span>
					<span class="block h-0.5 w-5 bg-current"></span>
					<span class="block h-0.5 w-5 bg-current"></span>
				</span>
			</button>
		</div>
	</header>

	{#if mobileMenuOpen}
		<button
			type="button"
			class="fixed inset-0 z-50 bg-black/40 lg:hidden"
			onclick={() => (mobileMenuOpen = false)}
			aria-label="Close menu"
		></button>
		<div class="fixed top-0 left-0 z-50 h-screen w-80 max-w-[85vw] bg-[#0b213b] p-5 text-slate-100 lg:hidden">
			<div class="mb-6 flex items-center justify-between">
				<a
					href="#services"
					aria-label="Home"
					title="Home"
					class="inline-flex h-12 w-12 items-center justify-center rounded-lg bg-white/10 text-white"
				>
					<svg
						xmlns="http://www.w3.org/2000/svg"
						viewBox="0 0 24 24"
						fill="none"
						stroke="currentColor"
						stroke-width="2"
						stroke-linecap="round"
						stroke-linejoin="round"
						class="h-6 w-6"
					>
						<path d="M3 10.5 12 3l9 7.5" />
						<path d="M5 9.5V21h14V9.5" />
						<path d="M9 21v-6h6v6" />
					</svg>
				</a>
				<button
					type="button"
					onclick={() => (mobileMenuOpen = false)}
					class="inline-flex h-9 w-9 items-center justify-center rounded-md bg-white/10"
					aria-label="Close menu"
				>
					X
				</button>
			</div>
			<nav class="space-y-2 text-sm">
				{#each menuLinks as link, index}
					<a
						href={link.href}
						onclick={() => (mobileMenuOpen = false)}
						class={`block rounded-lg border-l-2 border-transparent px-3 py-2 font-medium text-slate-100 transition hover:border-slate-400 hover:text-white ${link.bg} ${index % 2 === 0 ? 'shadow-[inset_0_1px_0_rgba(255,255,255,0.05)]' : ''}`}
					>
						<span class="inline-flex items-center gap-2">
							<svg
								xmlns="http://www.w3.org/2000/svg"
								viewBox="0 0 24 24"
								fill="none"
								stroke="currentColor"
								stroke-width="2"
								stroke-linecap="round"
								stroke-linejoin="round"
								class={`h-4 w-4 ${link.iconColor}`}
							>
								{#if link.icon === 'services'}
									<rect x="3" y="4" width="18" height="14" rx="2" />
									<path d="M8 20h8" />
								{:else if link.icon === 'offices'}
									<path d="M12 21s7-4.5 7-11a7 7 0 1 0-14 0c0 6.5 7 11 7 11Z" />
									<circle cx="12" cy="10" r="2.5" />
								{:else if link.icon === 'star'}
									<path d="m12 3 2.8 5.7 6.2.9-4.5 4.4 1.1 6.2L12 17.2 6.4 20.2l1.1-6.2L3 9.6l6.2-.9Z" />
								{:else if link.icon === 'rocket'}
									<path d="M5 19c2-1 3-2 4-4" />
									<path d="M15 5c3-1 6 2 5 5-1 3-4 6-7 7l-5-5c1-3 4-6 7-7Z" />
									<circle cx="14" cy="10" r="1" />
								{:else}
									<path d="M4 6h16v12H4z" />
									<path d="m4 8 8 5 8-5" />
								{/if}
							</svg>
							{link.label}
						</span>
					</a>
				{/each}
			</nav>
		</div>
	{/if}

	<div class="mx-auto max-w-6xl px-5 pt-24 pb-20 lg:ml-72 lg:max-w-none lg:px-10 lg:pt-14">
		<section id="services" class="py-2 sm:py-4">
			<img
				src="/imlg.png"
				alt="LexiconUSA logo"
				class="mb-8 w-full rounded-2xl bg-white/95 object-cover p-3"
			/>
			<h1 class="mx-auto max-w-4xl text-center text-3xl leading-tight font-semibold sm:text-5xl">
				Conference Interpretation Services for Multilingual Meetings That Need to Run Correctly
			</h1>
			<p class="mx-auto mt-6 max-w-4xl text-center text-base leading-relaxed text-slate-200 sm:text-lg">
				For over 30 years, LexiconUSA has been the simultaneous conference interpretation partner for
				organizations that will not accept anything less than complete accuracy. We support unions,
				associations, corporations, and government sessions with AIIC-level conference interpreters.
			</p>

			<div class="mt-8 flex flex-wrap justify-center gap-3">
				<Button href="https://www.lexiconusa.com/Simultaneous.html" target="_blank" rel="noreferrer" variant="outline">
					<svg
						xmlns="http://www.w3.org/2000/svg"
						viewBox="0 0 24 24"
						fill="none"
						stroke="currentColor"
						stroke-width="2"
						stroke-linecap="round"
						stroke-linejoin="round"
						class="mr-2 h-4 w-4"
					>
						<path d="M12 2a10 10 0 1 0 10 10" />
						<path d="M12 6v6l4 2" />
					</svg>
					25+ Years Experience</Button
				>
				<Button href="https://www.lexiconusa.com/Simultaneous.html" target="_blank" rel="noreferrer" variant="outline">
					<svg
						xmlns="http://www.w3.org/2000/svg"
						viewBox="0 0 24 24"
						fill="none"
						stroke="currentColor"
						stroke-width="2"
						stroke-linecap="round"
						stroke-linejoin="round"
						class="mr-2 h-4 w-4"
					>
						<circle cx="12" cy="12" r="9" />
						<path d="M8 12h8" />
						<path d="M12 8v8" />
					</svg>
					More than 75 Languages</Button
				>
				<Button
					href="https://www.lexiconusa.com/ContactUs-LexiconUSA.html"
					target="_blank"
					rel="noreferrer"
					variant="outline"
				>
					<svg
						xmlns="http://www.w3.org/2000/svg"
						viewBox="0 0 24 24"
						fill="none"
						stroke="currentColor"
						stroke-width="2"
						stroke-linecap="round"
						stroke-linejoin="round"
						class="mr-2 h-4 w-4"
					>
						<path d="M3 12a9 9 0 1 0 9-9" />
						<path d="M3 3v6h6" />
					</svg>
					Nationwide Service
				</Button>
			</div>

			<div class="mt-8 flex flex-wrap justify-center gap-3">
				<Button href="https://www.lexiconusa.com/Information.html" size="lg" class="border-2 border-black bg-[#175227] px-8 py-6 text-lg text-white hover:bg-[#123d1e]">
					Request a Quote | Call 1.888.283.2001
				</Button>
			</div>

		</section>

		<section id="offices" class="mt-10">
			<div class="mx-auto -mt-5 max-w-5xl rounded-3xl border-2 border-white/15 bg-transparent p-6">
				<h2 class="text-center text-2xl font-semibold sm:text-3xl">Major Languages</h2>
				<div class="mt-4 grid gap-2 text-sm sm:grid-cols-2 lg:grid-cols-4">
					<div class="flex items-center justify-center gap-3 rounded-lg bg-white/10 px-3 py-2">
						<span class="inline-flex h-5 w-5 items-center justify-center rounded-full bg-emerald-400 text-[11px] text-slate-950">✓</span>
						Spanish
					</div>
					<div class="flex items-center justify-center gap-3 rounded-lg bg-white/10 px-3 py-2">
						<span class="inline-flex h-5 w-5 items-center justify-center rounded-full bg-pink-400 text-[11px] text-slate-950">✓</span>
						French
					</div>
					<div class="flex items-center justify-center gap-3 rounded-lg bg-white/10 px-3 py-2">
						<span class="inline-flex h-5 w-5 items-center justify-center rounded-full bg-amber-300 text-[11px] text-slate-950">✓</span>
						German
					</div>
					<div class="flex items-center justify-center gap-3 rounded-lg bg-white/10 px-3 py-2">
						<span class="inline-flex h-5 w-5 items-center justify-center rounded-full bg-sky-400 text-[11px] text-slate-950">✓</span>
						Portuguese
					</div>
					<div class="flex items-center justify-center gap-3 rounded-lg bg-white/10 px-3 py-2">
						<span class="inline-flex h-5 w-5 items-center justify-center rounded-full bg-violet-400 text-[11px] text-slate-950">✓</span>
						Italian
					</div>
					<div class="flex items-center justify-center gap-3 rounded-lg bg-white/10 px-3 py-2">
						<span class="inline-flex h-5 w-5 items-center justify-center rounded-full bg-lime-300 text-[11px] text-slate-950">✓</span>
						Mandarin
					</div>
					<div class="flex items-center justify-center gap-3 rounded-lg bg-white/10 px-3 py-2">
						<span class="inline-flex h-5 w-5 items-center justify-center rounded-full bg-rose-400 text-[11px] text-slate-950">✓</span>
						Japanese
					</div>
					<div class="flex items-center justify-center gap-3 rounded-lg bg-white/10 px-3 py-2">
						<span class="inline-flex h-5 w-5 items-center justify-center rounded-full bg-cyan-300 text-[11px] text-slate-950">✓</span>
						Korean
					</div>
					<div class="flex items-center justify-center gap-3 rounded-lg bg-white/10 px-3 py-2">
						<span class="inline-flex h-5 w-5 items-center justify-center rounded-full bg-orange-400 text-[11px] text-slate-950">✓</span>
						Arabic
					</div>
					<div class="flex items-center justify-center gap-3 rounded-lg bg-white/10 px-3 py-2">
						<span class="inline-flex h-5 w-5 items-center justify-center rounded-full bg-teal-300 text-[11px] text-slate-950">✓</span>
						Russian
					</div>
					<div class="flex items-center justify-center gap-3 rounded-lg bg-white/10 px-3 py-2">
						<span class="inline-flex h-5 w-5 items-center justify-center rounded-full bg-fuchsia-400 text-[11px] text-slate-950">✓</span>
						Haitian Creole
					</div>
					<div class="flex items-center justify-center gap-2 rounded-lg bg-white/10 px-3 py-2">
						<span class="inline-flex h-5 w-5 items-center justify-center rounded-full bg-yellow-300 text-[11px] text-slate-950">✓</span>
						ASL
					</div>
				</div>
			</div>

			<div class="mx-auto max-w-5xl rounded-3xl border-2 border-white/15 bg-transparent p-6">
				<h2 class="mx-auto flex w-full items-center justify-center gap-2 text-center text-2xl font-semibold sm:text-3xl">
					<svg
						xmlns="http://www.w3.org/2000/svg"
						viewBox="0 0 24 24"
						fill="none"
						stroke="currentColor"
						stroke-width="2"
						stroke-linecap="round"
						stroke-linejoin="round"
						class="h-5 w-5 text-cyan-300"
						aria-hidden="true"
					>
						<circle cx="12" cy="12" r="9" />
						<path d="M3 12h18" />
						<path d="M12 3c2.8 3 4.5 6.4 4.5 9s-1.7 6-4.5 9c-2.8-3-4.5-6.4-4.5-9S9.2 6 12 3Z" />
					</svg>
					<span>Nationwide Service</span>
				</h2>
				<p class="mt-2 text-center text-slate-300">Quality, professional, local service.</p>
				<div class="mt-6 grid gap-2 text-sm sm:grid-cols-2 lg:grid-cols-4">
					{#each cities as city}
						<div class="rounded-lg bg-white/10 px-3 py-2">{city}</div>
					{/each}
				</div>
			</div>
		</section>

		<section id="what-sets-apart" class="mt-14">
			<h2 class="mx-auto text-center text-2xl font-semibold sm:text-3xl">What Sets LexiconUSA Apart</h2>

			<div class="mx-auto mt-8 max-w-5xl">
				<div class="grid items-center gap-8 lg:grid-cols-[280px_1fr] lg:gap-10">
					<div class="rounded-3xl bg-white/10 p-4 shadow-[0_18px_50px_rgba(0,0,0,0.18)] backdrop-blur-sm">
						<img
							src="https://www.lexiconusa.com/images/aiic-logo.png"
							alt="AIIC logo"
							class="mx-auto block h-auto w-full rounded-2xl bg-white p-3"
						/>
					</div>
					<div class="text-left">
						<div class="flex items-start gap-4">
							<div class="mt-1 inline-flex h-10 w-10 shrink-0 items-center justify-center rounded-full bg-white/10 text-white">
								<svg
									xmlns="http://www.w3.org/2000/svg"
									viewBox="0 0 24 24"
									fill="none"
									stroke="currentColor"
									stroke-width="2"
									stroke-linecap="round"
									stroke-linejoin="round"
									class="h-5 w-5"
								>
									<circle cx="12" cy="12" r="9" />
									<path d="M12 7v5l3 2" />
								</svg>
							</div>
							<p class="text-base leading-relaxed text-slate-200 sm:text-lg">
								Professional conference interpreters, exclusively. Every interpreter assigned meets the AIIC
								standard, the most rigorous independent benchmark in the profession, built over decades of
								global practice.
							</p>
						</div>
						<div class="mt-5 flex items-start gap-4">
							<div class="mt-1 inline-flex h-10 w-10 shrink-0 items-center justify-center rounded-full bg-white/10 text-white">
								<svg
									xmlns="http://www.w3.org/2000/svg"
									viewBox="0 0 24 24"
									fill="none"
									stroke="currentColor"
									stroke-width="2"
									stroke-linecap="round"
									stroke-linejoin="round"
									class="h-5 w-5"
								>
									<path d="M3 12a9 9 0 1 0 9-9" />
									<path d="M3 3v6h6" />
								</svg>
							</div>
							<p class="text-base leading-relaxed text-slate-200 sm:text-lg">
								Conference interpretation when experience matters. Subject-matched, fully prepared, and
								accountable through every session for unions, associations, corporations, and government
								meetings nationwide.
							</p>
						</div>
					</div>
				</div>
			</div>

			<div class="mt-8 grid gap-4 lg:grid-cols-3">
				<article class="rounded-2xl bg-white/10 p-4">
					<h3 class="font-semibold">Who We Serve</h3>
					<p class="mt-2 text-sm text-slate-200">
						NGOs, governments, tech companies, pharma, unions, associations, Fortune 100 corporations,
						and legal or arbitration proceedings.
					</p>
				</article>
				<article class="rounded-2xl bg-white/10 p-4">
					<h3 class="font-semibold">Session Accountability</h3>
					<p class="mt-2 text-sm text-slate-200">
						On-site technicians manage audio, equipment, and interpreter rotation while your project
						manager remains available from setup through final session.
					</p>
				</article>
				<article class="rounded-2xl bg-white/10 p-4">
					<h3 class="font-semibold">One Team, One Contact</h3>
					<p class="mt-2 text-sm text-slate-200">
						When something needs attention, it is handled before your audience is aware. One team,
						one accountability path.
					</p>
				</article>
			</div>
		</section>

		<Button
			href="https://www.lexiconusa.com/Simultaneous-Form.html"
			variant="secondary"
			size="lg"
			class="mt-14 block h-auto rounded-3xl border-2 border-black bg-[#175227] p-6 text-center text-white hover:bg-[#123d1e] sm:p-10"
		>
			<span class="block text-3xl leading-tight font-semibold sm:text-4xl">Get Started Today</span>
			<span class="mx-auto mt-3 block max-w-2xl text-center text-white/80">
				Make your next event a success with a trusted leader in simultaneous interpretation and
				conference interpretation.
			</span>
			<span class="mt-7 inline-flex rounded-full border border-black bg-black px-6 py-3 text-sm font-semibold text-white">
				GET STARTED Today
			</span>
		</Button>

		<footer id="contact" class="mt-14 pb-8">
			<div class="grid gap-8 lg:grid-cols-[1.2fr_1fr_1fr_1fr]">
				<section>
					<img src="/LexiconUSA.png" alt="LexiconUSA" class="h-14 w-auto" />
					<p class="mt-4 text-sm text-slate-200">
						We are a professional conference interpretation company specializing in international
						conference production and the sale and rental of interpretation equipment.
					</p>
					<p class="mt-4 text-sm"><strong>Tech Support:</strong> <a href="tel:+18882832001">1.888.283.2001</a></p>
					<p class="mt-2 text-sm"><strong>24/7 Support:</strong> Chat with Us</p>
					<p class="mt-2 text-sm">
						<strong>Support Documents:</strong>
						<a href="https://www.lexiconusa.com/support/" target="_blank" rel="noreferrer">Click Here</a>
					</p>
					<p class="mt-2 text-sm">
						<strong>Privacy Policy and Terms of Use:</strong>
						<a href="https://lexiconusa.com/Terms-and-Services.html" target="_blank" rel="noreferrer"
							>Click Here</a
						>
					</p>
				</section>

				<section>
					<h3 class="flex items-center gap-2 text-sm font-semibold tracking-wide uppercase">
						<svg
							xmlns="http://www.w3.org/2000/svg"
							viewBox="0 0 24 24"
							fill="none"
							stroke="currentColor"
							stroke-width="2"
							stroke-linecap="round"
							stroke-linejoin="round"
							class="h-4 w-4 text-cyan-300"
						>
							<path d="M4 6h16v12H4z" />
							<path d="m4 8 8 5 8-5" />
						</svg>
						LexiconUSA Services
					</h3>
					<ul class="mt-3 space-y-2 text-sm text-slate-200">
						<li><a href="https://www.lexiconusa.com/Simultaneous.html" target="_blank" rel="noreferrer">Conference Interpretation</a></li>
						<li><a href="https://www.lexiconusa.com/Video-Translation.html" target="_blank" rel="noreferrer">Remote Interpretation</a></li>
						<li><a href="https://www.lexiconusa.com/Doument-Translation.html" target="_blank" rel="noreferrer">Document Translation</a></li>
						<li><a href="https://www.lexiconusa.com/Video-Translation.html" target="_blank" rel="noreferrer">Video Translation</a></li>
						<li><a href="https://www.lexiconusa.com/Rentals/Meeting-System-Rental.html" target="_blank" rel="noreferrer">Complete Audio Visual Equipment</a></li>
						<li><a href="https://www.lexiconusa.com/Rentals/Rental-Catalog-Translation-Equipment.html" target="_blank" rel="noreferrer">Translation Equipment</a></li>
						<li><a href="https://www.lexiconusa.com/Consulting.html" target="_blank" rel="noreferrer">Event Consulting</a></li>
					</ul>
				</section>

				<section>
					<h3 class="flex items-center gap-2 text-sm font-semibold tracking-wide uppercase">
						<svg
							xmlns="http://www.w3.org/2000/svg"
							viewBox="0 0 24 24"
							fill="none"
							stroke="currentColor"
							stroke-width="2"
							stroke-linecap="round"
							stroke-linejoin="round"
							class="h-4 w-4 text-cyan-300"
						>
							<path d="M12 2 5 6v6c0 5 3.5 8 7 10 3.5-2 7-5 7-10V6Z" />
							<path d="M9 12l2 2 4-4" />
						</svg>
						Translation Equipment
					</h3>
					<ul class="mt-3 space-y-2 text-sm text-slate-200">
						<li><a href="https://www.lexiconusa.com/Systems/Translation-Equipment-Systems-Page.html" target="_blank" rel="noreferrer">Buy Translation Equipment</a></li>
						<li><a href="https://www.lexiconusa.com/Rentals/Rental-Catalog-Translation-Equipment.html" target="_blank" rel="noreferrer">Rent Translation Equipment</a></li>
						<li><a href="https://www.lexiconusa.com/Rentals/Meeting-System-Rental.html" target="_blank" rel="noreferrer">Audio and Video Equipment</a></li>
					</ul>
				</section>

				<section>
					<h3 class="flex items-center gap-2 text-sm font-semibold tracking-wide uppercase">
						<svg
							xmlns="http://www.w3.org/2000/svg"
							viewBox="0 0 24 24"
							fill="none"
							stroke="currentColor"
							stroke-width="2"
							stroke-linecap="round"
							stroke-linejoin="round"
							class="h-4 w-4 text-cyan-300"
						>
							<path d="M12 21s7-4.5 7-11a7 7 0 1 0-14 0c0 6.5 7 11 7 11Z" />
							<circle cx="12" cy="10" r="2.5" />
						</svg>
						Regional Offices
					</h3>
					<div class="mt-3 space-y-3 text-sm text-slate-200">
						<p><strong>Los Angeles:</strong> 11601 Wilshire Blvd, 5th Floor, Los Angeles, CA 90025, <a href="tel:+13236949860">323.694.9860</a>, <a href="mailto:info@LexiconUSA.com">info@LexiconUSA.com</a></p>
						<p><strong>New York:</strong> 100 Church Street, 8th Floor, New York, NY 10007, <a href="tel:+16464928050">646.492.8050</a>, <a href="mailto:NYC@LexiconUSA.com">NYC@LexiconUSA.com</a></p>
						<p><strong>Chicago:</strong> 1821 Walden Office Square, Suite 405, Schaumburg, IL 60173, <a href="tel:+13127864750">312.786.4750</a>, <a href="mailto:CHI@LexiconUSA.com">CHI@LexiconUSA.com</a></p>
						<p><strong>Honolulu:</strong> Waterfront Plaza, 500 Ala Moana Blvd, Suite 405, Honolulu, HI 96813, <a href="tel:+18084513500">808.451.3500</a>, <a href="mailto:Info@LexiconUSA.com">Hon@LexiconUSA.com</a></p>
						<p><strong>Las Vegas:</strong> 3960 Howard Hughes Pkwy, Suite 515, Las Vegas, NV 891691, <a href="tel:+17029977770">702.997.7770</a>, <a href="mailto:Info@LexiconUSA.com">LAS@LexiconUSA.com</a></p>
						<p><strong>Bay Area:</strong> 800 W El Camino Real, Suite 185, Mountain View, CA 94040, <a href="tel:+16504608400">650.460.8400</a>, <a href="mailto:Info@LexiconUSA.com">Info@LexiconUSA.com</a></p>
					</div>
				</section>
			</div>

			<p class="mt-8 flex items-center gap-2 pt-4 text-xs text-slate-300">
				<svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.8" stroke-linecap="round" stroke-linejoin="round" class="h-4 w-4 shrink-0 text-cyan-300" aria-hidden="true">
					<circle cx="12" cy="12" r="9" />
					<path d="M15.5 9.5a4 4 0 1 0 0 5" />
				</svg>
				<span>Copyright 2017 LexiconUSA. All rights reserved.</span>
			</p>
		</footer>
	</div>

	{#if showBackToTop}
		<a
			href="#top"
			aria-label="Back to top"
			title="Back to top"
			class="fixed right-5 bottom-5 z-50 inline-flex items-center gap-2 rounded-full border border-cyan-200/30 bg-[#0b213b]/90 px-4 py-3 text-sm font-semibold text-slate-100 shadow-[0_18px_40px_rgba(0,0,0,0.35)] backdrop-blur transition hover:-translate-y-0.5 hover:bg-[#12365f]"
		>
			<img src="/fav.png" alt="" aria-hidden="true" class="h-5 w-5" />
			<span>Back to top</span>
		</a>
	{/if}
</main>
