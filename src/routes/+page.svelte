<script>
	import { onMount } from 'svelte';

	let scrollY = 0;
	let navVisible = false;
	let mounted = false;

	const projects = [
		{
			id: 1,
			title: 'Insurance Management Platform',
			stack: ['Go', 'Spring Boot', 'PostgreSQL', 'Docker'],
			desc: 'Backend engine powering automated policy lifecycles, digital onboarding, and systemic renewals across multiple insurance product lines.',
			year: '2026'
		},
		{
			id: 2,
			title: 'Mojaloop Connector Services',
			stack: ['Go', 'gRPC', 'Kafka', 'Redis'],
			desc: 'High-throughput, distributed payment interoperability layer for seamless DFSP network integrations and real-time settlement processing.',
			year: '2024'
		},
		{
			id: 3,
			title: 'Multi-Tenant School Architecture',
			stack: ['Go', 'React', 'PostgreSQL', 'Redis'],
			desc: 'SaaS education ecosystem with an optimized Go backend and modular React interface for scalable multi-tenant management.',
			year: '2025'
		}
	];

	const stack = [
		'Go',
		'TypeScript',
		'Laravel PHP',
		'PostgreSQL',
		'Redis',
		'Docker',
		'Kubernetes',
		'REST APIs',
		'Spring Boot',
		'React',
        'Remix',
        'Angular'
	];

	onMount(() => {
		mounted = true;

		const handleScroll = () => {
			scrollY = window.scrollY;
			navVisible = scrollY > window.innerHeight * 0.6;
		};

		window.addEventListener('scroll', handleScroll, { passive: true });

		const observer = new IntersectionObserver(
			(entries) => entries.forEach((e) => e.isIntersecting && e.target.classList.add('visible')),
			{ threshold: 0.08, rootMargin: '0px 0px -40px 0px' }
		);

		document.querySelectorAll('.reveal').forEach((el) => observer.observe(el));

		return () => {
			window.removeEventListener('scroll', handleScroll);
			observer.disconnect();
		};
	});
</script>

<svelte:head>
	<title>Mwansa Mwansa — Full-Stack Engineer</title>
</svelte:head>

<!-- Fixed Navigation -->
<nav
	class="fixed left-0 right-0 top-0 z-50 flex items-center justify-between px-8 py-5 md:px-16 {navVisible
		? 'bg-[#060614]/85 backdrop-blur-xl border-b border-white/8'
		: ''}"
	style="transition: background-color 0.5s ease, border-color 0.5s ease;"
>
	<a href="#top" class="font-mono text-sm font-medium tracking-widest text-neutral-200">M.</a>
	<div class="flex gap-8 text-xs font-medium uppercase tracking-widest text-neutral-400">
		<a href="#work" class="transition-colors duration-300 hover:text-neutral-100">Work</a>
		<a href="#stack" class="transition-colors duration-300 hover:text-neutral-100">Stack</a>
		<a href="#contact" class="transition-colors duration-300 hover:text-neutral-100">Contact</a>
	</div>
</nav>

<!-- Root -->
<div
	id="top"
	class="relative overflow-x-hidden bg-[#060614] text-neutral-50 antialiased"
>
	<!-- Parallax Background Orbs -->
	<div class="pointer-events-none fixed inset-0 z-0 overflow-hidden">
		<div
			class="absolute -left-32 -top-32 h-150 w-150 rounded-full blur-[120px]"
			style="background: radial-gradient(circle, rgba(99,102,241,0.18), rgba(59,130,246,0.08), transparent); transform: translateY({scrollY * 0.06}px)"
		></div>
		<div
			class="absolute -right-48 top-[25vh] h-125 w-125 rounded-full blur-[100px]"
			style="background: radial-gradient(circle, rgba(129,140,248,0.12), rgba(99,102,241,0.06), transparent); transform: translateY({scrollY * 0.04}px)"
		></div>
		<div
			class="absolute bottom-0 left-1/3 h-100 w-100 rounded-full blur-[130px]"
			style="background: radial-gradient(circle, rgba(167,139,250,0.1), rgba(99,102,241,0.05), transparent); transform: translateY({scrollY * 0.08}px)"
		></div>
		<div
			class="absolute left-1/2 top-[15vh] h-87.5 w-87.5 rounded-full blur-[100px]"
			style="background: radial-gradient(circle, rgba(56,189,248,0.07), rgba(99,102,241,0.05), transparent); transform: translateX(-50%) translateY({scrollY * 0.05}px)"
		></div>
	</div>

	<!-- Dot grid -->
	<div
		class="pointer-events-none fixed inset-0 z-0"
		style="background-image: radial-gradient(circle, rgba(99,102,241,0.15) 1px, transparent 1px); background-size: 28px 28px; opacity: 0.35;"
	></div>

	<!-- ====== HERO ====== -->
	<section class="relative z-10 flex min-h-screen flex-col justify-center px-8 pb-20 pt-24 md:px-16">
		<div
			class="relative z-10 max-w-4xl"
			style="transform: translateY({scrollY * 0.14}px); opacity: {mounted
				? Math.max(0, 1 - scrollY / 550)
				: 1}"
		>
			<!-- Label -->
			<div class="animate-fade-up mb-8 flex items-center gap-3">
				<div class="h-px w-8 bg-indigo-400"></div>
				<span class="font-mono text-[11px] uppercase tracking-[0.25em] text-indigo-400"
					>Full-Stack Engineer</span
				>
			</div>

			<!-- Name -->
			<h1
				class="animate-fade-up-delay-1 font-light leading-[0.88] tracking-[-0.04em]"
				style="font-size: clamp(3.5rem, 10vw, 8rem);"
			>
				Mwansa
				<span
					class="block text-transparent"
					style="background: linear-gradient(135deg, #c4b5fd, #818cf8, #60a5fa); -webkit-background-clip: text; background-clip: text;"
				>
					Mwansa
				</span>
			</h1>

			<!-- Tagline -->
			<p
				class="animate-fade-up-delay-2 mt-10 max-w-xl font-light leading-relaxed text-neutral-300"
				style="font-size: clamp(0.9rem, 1.4vw, 1.05rem);"
			>
				Backend-first full-stack engineer — Go APIs and distributed systems on the server,
				React and TypeScript on the client. Specialising in fintech infrastructure and
				high-concurrency systems end to end.
			</p>

			<!-- CTAs -->
			<div class="animate-fade-up-delay-3 mt-12 flex items-center gap-6">
				<a
					href="#work"
					class="group inline-flex items-center gap-3 rounded border border-neutral-600 px-5 py-3 text-xs font-medium uppercase tracking-widest text-neutral-100 transition-all duration-300 hover:border-indigo-400/70 hover:bg-indigo-500/10 hover:text-indigo-300"
				>
					View Work
					<span class="text-indigo-400 transition-transform duration-300 group-hover:translate-x-1"
						>→</span
					>
				</a>
				<a
					href="#contact"
					class="text-xs font-medium uppercase tracking-widest text-neutral-500 transition-colors duration-300 hover:text-neutral-200"
				>
					Connect
				</a>
			</div>
		</div>

		<!-- Scroll indicator -->
		<div
			class="absolute bottom-10 left-8 flex flex-col items-center gap-3 md:left-16"
			style="opacity: {mounted ? Math.max(0, 1 - scrollY / 280) : 1}"
		>
			<div class="scroll-line h-14 w-px bg-gradient-to-b from-transparent via-neutral-500 to-transparent"></div>
			<span class="font-mono text-[9px] uppercase tracking-[0.3em] text-neutral-500">Scroll</span>
		</div>
	</section>

	<!-- ===== WORK ===== -->
	<section id="work" class="relative z-20 bg-[#060614] px-8 pb-16 pt-28 md:px-16">
		<div class="mx-auto max-w-5xl">
			<!-- Section header -->
			<div class="reveal mb-20 flex items-center gap-5">
				<span class="font-mono text-[10px] uppercase tracking-[0.3em] text-neutral-400">01</span>
				<div class="h-px flex-1 bg-neutral-700/50"></div>
				<span class="font-mono text-[10px] uppercase tracking-[0.3em] text-neutral-400"
					>Selected Work</span
				>
			</div>

			<!-- Project rows -->
			<div>
				{#each projects as project, i (project.id)}
					<div
						class="reveal group relative grid gap-6 border-t border-neutral-800 py-12 transition-colors duration-500 hover:border-neutral-700 md:grid-cols-12 md:gap-10"
						style="transition-delay: {i * 80}ms"
					>
						<!-- Index + year -->
						<div class="flex flex-row items-start gap-4 md:col-span-2 md:flex-col md:gap-2">
							<span
								class="font-mono text-xs text-neutral-500 transition-colors duration-300 group-hover:text-indigo-400"
							>
								0{project.id}
							</span>
							<span class="font-mono text-xs text-neutral-500">{project.year}</span>
						</div>

						<!-- Title + stack -->
						<div class="md:col-span-4">
							<h3
								class="font-light leading-snug tracking-tight text-neutral-100 transition-colors duration-300 group-hover:text-white"
								style="font-size: clamp(1rem, 1.5vw, 1.2rem);"
							>
								{project.title}
							</h3>
							<div class="mt-4 flex flex-wrap gap-2">
								{#each project.stack as tech (tech)}
									<span
										class="rounded border border-neutral-700 px-2 py-1 font-mono text-[10px] uppercase tracking-widest text-neutral-400 transition-all duration-300 group-hover:border-indigo-500/40 group-hover:text-neutral-300"
									>
										{tech}
									</span>
								{/each}
							</div>
						</div>

						<!-- Description -->
						<div class="flex items-center md:col-span-6">
							<p
								class="font-light leading-relaxed text-neutral-400 transition-colors duration-300 group-hover:text-neutral-300"
								style="font-size: 0.875rem;"
							>
								{project.desc}
							</p>
						</div>

						<!-- Bottom accent line on hover -->
						<div
							class="absolute bottom-0 left-0 h-px w-0 bg-gradient-to-r from-indigo-400/60 to-transparent transition-all duration-700 group-hover:w-full"
						></div>
					</div>
				{/each}
				<div class="border-t border-neutral-800"></div>
			</div>
		</div>
	</section>

	<!-- ===== STACK ===== -->
	<section id="stack" class="relative z-20 bg-[#060614] px-8 py-24 md:px-16">
		<div class="mx-auto max-w-5xl">
			<!-- Section header -->
			<div class="reveal mb-16 flex items-center gap-5">
				<span class="font-mono text-[10px] uppercase tracking-[0.3em] text-neutral-400">02</span>
				<div class="h-px flex-1 bg-neutral-700/50"></div>
				<span class="font-mono text-[10px] uppercase tracking-[0.3em] text-neutral-400"
					>Core Stack</span
				>
			</div>

			<!-- Grid -->
			<div
				class="reveal grid grid-cols-3 overflow-hidden rounded-lg border border-neutral-700/60 bg-neutral-800/40 md:grid-cols-4 lg:grid-cols-6"
				style="gap: 1px;"
			>
				{#each stack as tech (tech)}
					<div
						class="group flex items-center justify-center bg-[#060614] px-4 py-6 transition-colors duration-300 hover:bg-indigo-500/5"
					>
						<span
							class="text-center font-mono text-[10px] uppercase tracking-widest text-neutral-400 transition-colors duration-300 group-hover:text-indigo-300"
						>
							{tech}
						</span>
					</div>
				{/each}
			</div>
		</div>
	</section>

	<!-- ===== CONTACT ===== -->
	<section id="contact" class="relative z-20 bg-[#060614] px-8 py-24 md:px-16">
		<div class="mx-auto max-w-5xl">
			<!-- Section header -->
			<div class="reveal mb-20 flex items-center gap-5">
				<span class="font-mono text-[10px] uppercase tracking-[0.3em] text-neutral-400">03</span>
				<div class="h-px flex-1 bg-neutral-700/50"></div>
				<span class="font-mono text-[10px] uppercase tracking-[0.3em] text-neutral-400"
					>Get In Touch</span
				>
			</div>

			<div class="grid items-end gap-16 md:grid-cols-2">
				<!-- Left: availability -->
				<div class="reveal">
					<p
						class="font-light leading-relaxed tracking-tight text-neutral-200"
						style="font-size: clamp(1.25rem, 2.5vw, 1.75rem);"
					>
						Open to Full-Stack or Go engineering roles globally — backend, frontend, or anywhere in between.
					</p>
					<p class="mt-4 text-sm font-light text-neutral-500">Remote · Hybrid · On-site</p>
				</div>

				<!-- Right: links -->
				<div class="reveal flex flex-col items-start gap-6 md:items-end">
					<a
						href="mailto:mwansammwansa@gmail.com"
						class="group relative font-light text-neutral-200 transition-colors duration-300 hover:text-indigo-300"
						style="font-size: clamp(1rem, 1.8vw, 1.25rem);"
					>
						mwansammwansa@gmail.com
						<span
							class="absolute -bottom-0.5 left-0 h-px w-0 origin-left bg-gradient-to-r from-indigo-400 to-blue-400 transition-all duration-500 group-hover:w-full"
						></span>
					</a>

					<div class="flex gap-6 font-mono text-xs uppercase tracking-widest text-neutral-400">
						<a
							href="https://linkedin.com/in/mwansa-mwansa"
							target="_blank"
							rel="noopener noreferrer"
							class="transition-colors duration-300 hover:text-indigo-300"
						>
							LinkedIn
						</a>
						<a
							href="https://github.com/mwansa-mwansa"
							target="_blank"
							rel="noopener noreferrer"
							class="transition-colors duration-300 hover:text-indigo-300"
						>
							GitHub
						</a>
					</div>
				</div>
			</div>
		</div>
	</section>

	<!-- Footer -->
	<footer class="relative z-20 border-t border-neutral-800 bg-[#060614] px-8 py-8 md:px-16">
		<div class="mx-auto flex max-w-5xl items-center justify-between">
			<span class="font-mono text-xs text-neutral-500">Mwansa Mwansa</span>
			<span class="font-mono text-xs text-neutral-500">
				{new Date().getFullYear()}
			</span>
		</div>
	</footer>

	<!-- Back to top -->
	<button
		onclick={() => window.scrollTo({ top: 0, behavior: 'smooth' })}
		aria-label="Back to top"
		class="fixed bottom-8 right-8 z-50 flex h-10 w-10 items-center justify-center rounded border border-neutral-700 bg-[#060614] font-mono text-sm text-neutral-400 transition-all duration-300 hover:border-indigo-500/60 hover:text-indigo-400 md:bottom-10 md:right-10"
		style="opacity: {scrollY > 400 ? 1 : 0}; pointer-events: {scrollY > 400 ? 'auto' : 'none'}; transform: translateY({scrollY > 400 ? 0 : 8}px);"
	>
		↑
	</button>
</div>
